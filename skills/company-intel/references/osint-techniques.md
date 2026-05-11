# OSINT Techniques Reference

Technical open-source intelligence techniques for company research. Used primarily during Phase 8 (Digital Footprint) but applicable across all phases requiring technical reconnaissance.

---

## 1. DNS and Infrastructure Reconnaissance

DNS records are the foundational layer of any company's internet presence. They reveal hosting choices, email providers, third-party integrations, and operational sophistication — often far more than the company intends to make public.

### A/AAAA Records — Hosting Provider Identification

**What it is:** A records map a domain to an IPv4 address; AAAA records map to IPv6. The IP address reveals the hosting provider.

**Why it matters:** Hosting choices signal budget, technical maturity, and sometimes regulatory posture. A company on AWS or GCP likely has engineering resources; a company on a shared hosting plan signals a smaller operation. On-premises hosting may indicate data sensitivity requirements or legacy infrastructure.

**How to do it:**
```
dig A company.com
dig AAAA company.com
```
Cross-reference the returned IP against:
- AWS IP ranges: https://ip-ranges.amazonaws.com/ip-ranges.json
- Azure IP ranges: https://www.microsoft.com/en-us/download/details.aspx?id=56519
- GCP IP ranges: https://www.gstatic.com/ipranges/cloud.json
- Cloudflare: typically 104.x.x.x or 172.64-67.x.x ranges
- Use `whois <IP>` for general provider identification

### MX Records — Email Provider

**What it is:** MX records specify the mail servers handling email for the domain.

**Why it matters:** Email provider reveals organisational tooling ecosystem and sometimes budget. Google Workspace and Microsoft 365 are the dominant business email platforms; self-hosted mail servers suggest either strong technical capacity or outdated infrastructure; Protonmail signals privacy consciousness.

**How to do it:**
```
dig MX company.com
```
Common patterns:
- `aspmx.l.google.com` → Google Workspace
- `company-com.mail.protection.outlook.com` → Microsoft 365
- `mail.protonmail.ch` → Protonmail
- `inbound-smtp.*.amazonaws.com` → Amazon WorkMail or SES
- Custom hostnames on company domain → self-hosted

### TXT Records — SPF/DKIM/DMARC and Third-Party Verification

**What it is:** TXT records contain arbitrary text data, most commonly used for email authentication (SPF, DKIM, DMARC) and domain ownership verification for third-party services.

**Why it matters:** TXT records are one of the richest single sources of OSINT. SPF records list every service authorised to send email on behalf of the domain — effectively a manifest of their email-sending tools. Verification strings reveal which SaaS platforms the company uses.

**How to do it:**
```
dig TXT company.com
```

**SPF record interpretation example:**
```
v=spf1 include:_spf.google.com include:servers.mcsv.net include:sendgrid.net ~all
```
This decodes to:
- `include:_spf.google.com` → Google Workspace (primary email)
- `include:servers.mcsv.net` → Mailchimp (email marketing)
- `include:sendgrid.net` → SendGrid (transactional email)
- `~all` → soft fail (permissive policy; stricter would be `-all`)

**Common SPF includes and what they reveal:**
| SPF Include | Service |
|---|---|
| `_spf.google.com` | Google Workspace |
| `spf.protection.outlook.com` | Microsoft 365 |
| `servers.mcsv.net` | Mailchimp |
| `sendgrid.net` | SendGrid / Twilio |
| `amazonses.com` | Amazon SES |
| `spf.mandrillapp.com` | Mandrill (Mailchimp transactional) |
| `mktomail.com` | Marketo |
| `spf.hubspot.com` | HubSpot |
| `zendesk.com` | Zendesk |
| `freshdesk.com` | Freshdesk |
| `salesforce.com` | Salesforce |
| `_spf.salesforce.com` | Salesforce |
| `spf.messagelabs.com` | Symantec Email Security |

**Common verification TXT records:**
| TXT Record Pattern | Service |
|---|---|
| `google-site-verification=...` | Google Search Console |
| `MS=ms...` | Microsoft 365 |
| `facebook-domain-verification=...` | Facebook Business |
| `atlassian-domain-verification=...` | Atlassian (Jira/Confluence) |
| `hubspot-developer-verification=...` | HubSpot |
| `apple-domain-verification=...` | Apple Business |
| `docusign=...` | DocuSign |
| `stripe-verification=...` | Stripe |
| `_dmarc...` | DMARC policy record |
| `v=DMARC1; p=reject; ...` | Strict DMARC enforcement |

### CNAME Records — Subdomain Service Mapping

**What it is:** CNAME records alias one domain name to another, commonly used to point subdomains at third-party services.

**Why it matters:** CNAMEs reveal the specific tools a company uses for support, documentation, status pages, marketing, and more. Each subdomain-to-service mapping adds to the technology profile.

**How to do it:**
```
dig CNAME mail.company.com
dig CNAME support.company.com
dig CNAME help.company.com
dig CNAME status.company.com
dig CNAME docs.company.com
dig CNAME blog.company.com
dig CNAME app.company.com
dig CNAME api.company.com
```

Common CNAME targets:
| Subdomain | CNAME Target | Service |
|---|---|---|
| `support.` | `company.zendesk.com` | Zendesk |
| `help.` | `company.freshdesk.com` | Freshdesk |
| `status.` | `xxxxx.statuspage.io` | Atlassian Statuspage |
| `docs.` | `company.readme.io` | ReadMe |
| `blog.` | `xxx.ghost.io` | Ghost CMS |
| `blog.` | `domains.squarespace.com` | Squarespace |
| `app.` | `xxx.herokuapp.com` | Heroku |

### NS Records — DNS Management

**What it is:** NS records identify the authoritative name servers for the domain.

**Why it matters:** DNS provider choice indicates infrastructure sophistication. Cloudflare NS records suggest the company uses Cloudflare for CDN/security. AWS Route 53 suggests deep AWS integration. A registrar's default nameservers (e.g., `ns1.domaincontrol.com` for GoDaddy) suggest minimal DNS management investment.

**How to do it:**
```
dig NS company.com
```

### SOA Records — Management Activity

**What it is:** SOA (Start of Authority) records contain administrative information about the DNS zone, including serial number, refresh intervals, and responsible party email.

**Why it matters:** The serial number format can indicate DNS management tooling (date-based serials like `2024010101` vs arbitrary incrementing numbers). The responsible party email (RNAME field) sometimes reveals an admin contact. Refresh and retry intervals indicate management attention to DNS propagation.

**How to do it:**
```
dig SOA company.com
```

### Subdomain Enumeration via Certificate Transparency

**What it is:** Certificate Transparency (CT) is a public logging framework for SSL/TLS certificates. Every certificate issued by a participating CA is logged, including the domain names it covers. crt.sh provides a searchable interface over these logs.

**Why it matters:** CT logs reveal subdomains the company has obtained certificates for, including internal tools, staging environments, and services they may not publicly advertise. This often surfaces more subdomains than any other single technique.

**How to do it:**
```
https://crt.sh/?q=%.company.com
```
The `%` wildcard matches any subdomain. Review results for:
- Internal tool names (jira., confluence., grafana., kibana., jenkins.)
- Environment indicators (staging., dev., uat., preprod.)
- Acquired brands or products on separate subdomains
- API endpoints (api., api-v2., graphql.)
- Regional variants (au., us., eu.)

---

## 2. SSL/TLS Certificate Intelligence

SSL/TLS certificates are public records that contain structured metadata about the organisation and its domain infrastructure.

### Certificate Transparency Log Analysis

**What it is:** Querying CT logs (primarily via crt.sh) to build a comprehensive picture of a company's certificate history.

**Why it matters:** Certificates are issued over time, so the log shows infrastructure evolution — new services appearing, old ones being decommissioned, rebrands, and acquisitions.

**How to do it:**
```
https://crt.sh/?q=%.company.com&output=json
```
The JSON output can be parsed programmatically. Track:
- New subdomains appearing over time (service launches)
- Certificates that stopped being renewed (service shutdowns)
- Issuer changes (security posture evolution)

### SAN (Subject Alternative Names)

**What it is:** A single certificate can cover multiple domain names listed in the SAN field.

**Why it matters:** SANs reveal related domains the company controls. A certificate for `company.com` might also list `companyapp.com`, `company.io`, `acquiredstartup.com`, and `internal-tools.company.com`. This is one of the most reliable ways to discover related domains and acquisitions.

**How to do it:**
Click into any certificate on crt.sh and examine the "Subject Alternative Names" or "DNS Names" section. Look for:
- Alternative TLDs (.com, .com.au, .io, .co, .org)
- Product-specific domains
- Acquired company domains
- Country-specific domains

### Certificate Authority Selection

**What it is:** Which CA issued the certificate (Let's Encrypt, DigiCert, Sectigo, AWS Certificate Manager, etc.).

**Why it matters:** CA choice signals operational maturity and budget:
- **Let's Encrypt**: Free, automated — common for startups and tech-savvy orgs
- **DigiCert/Sectigo**: Paid, often used by enterprises with compliance requirements
- **AWS Certificate Manager**: Deep AWS integration
- **Cloudflare Origin CA**: Using Cloudflare as CDN/proxy
- **EV (Extended Validation) certificates**: Expensive, require legal verification — signals corporate formality

### Certificate History and Issuance Patterns

**What it is:** Tracking the timeline of certificate issuance, renewal, and expiry.

**Why it matters:** Irregular patterns (expired certificates, sudden CA changes, long gaps) can indicate organisational disruption. Automated 90-day renewal cycles (Let's Encrypt) indicate good DevOps practices. Manual annual renewals with occasional lapses indicate less automation.

### Wildcard vs Individual Certificates

**What it is:** Whether the company uses `*.company.com` wildcard certificates or individual certificates per subdomain.

**Why it matters:** Wildcard certificates obscure the actual subdomains in use (since only `*.company.com` appears in CT logs rather than each individual subdomain). If a company uses wildcards, CT-based subdomain enumeration will be less effective. Individual certificates provide a richer picture of infrastructure.

---

## 3. WHOIS and Domain Intelligence

WHOIS records are the registration data for domain names — the digital equivalent of a property title search.

### Standard WHOIS Data Extraction

**What it is:** Querying the WHOIS database for a domain's registration details.

**Why it matters:** WHOIS can reveal registrant name, organisation, contact email, registration date, expiry date, registrar, and name servers. Even with GDPR-related redaction becoming common, useful data often remains — particularly for older registrations and non-EU domains.

**How to do it:**
```
whois company.com
```
Key fields to extract:
- **Registrant Organisation**: Legal entity name (may differ from trading name)
- **Registrant Email**: Contact email (sometimes personal)
- **Creation Date**: How long the company has owned this domain
- **Updated Date**: Most recent change (may indicate ownership transfer)
- **Registrar**: Domain registrar choice
- **Name Servers**: Cross-reference with NS record analysis

### Historical WHOIS

**What it is:** Archived WHOIS records showing how registration data has changed over time.

**Why it matters:** Historical WHOIS reveals ownership transfers (acquisitions), contact changes, registrar migrations, and when privacy protection was enabled. If a domain was registered by an individual before being transferred to a company, the individual may be a founder.

**How to do it:**
- **DomainTools**: https://whois.domaintools.com/ (paid, most comprehensive)
- **WhoisXMLAPI**: https://www.whoisxmlapi.com/ (paid API)
- **Whoxy**: https://www.whoxy.com/ (partial free access)
- **Wayback Machine WHOIS**: Sometimes archived in page snapshots

### Reverse WHOIS

**What it is:** Searching for all domains registered by the same entity (name, email, organisation, phone number).

**Why it matters:** Reveals the full portfolio of domains owned by a company or individual — including product domains, holding company domains, parked domains for future projects, and domains related to acquisitions. Essential for mapping the complete digital footprint.

**How to do it:**
- DomainTools Reverse WHOIS
- ViewDNS.info: https://viewdns.info/reversewhois/
- Whoxy Reverse WHOIS API
- Search by registrant email, registrant name, or registrant organisation

### auDA WHOIS for .com.au / .au Domains

**What it is:** The .au domain space is managed by auDA (au Domain Administration) and has richer WHOIS data requirements than generic TLDs.

**Why it matters:** Australian domain registrations require an eligible entity (ABN/ACN holder) and often include the registrant's ABN or ACN directly in WHOIS data. This provides a direct link to ASIC/ABR records and confirms the legal entity behind the domain.

**How to do it:**
```
whois company.com.au
```
Look for:
- Registrant Name (legal entity)
- Registrant ID (often the ABN or ACN)
- Eligibility Type (Company, Business, etc.)
- Eligibility ID (ABN/ACN)

### Domain Age and Registration Patterns

**What it is:** Analysing when domains were registered relative to the company's claimed history.

**Why it matters:** A company claiming to have been established in 2005 but with a domain registered in 2019 raises questions. Similarly, a flurry of domain registrations may precede a product launch or rebrand. Domains registered well before a company was incorporated may indicate personal projects that became businesses.

---

## 4. Cloud Footprint Detection

Identifying which cloud providers and services a company uses, even when they attempt to abstract this behind their own domain.

### IP Range Analysis

**What it is:** Comparing the company's resolved IP addresses against the published IP ranges of major cloud providers.

**Why it matters:** Confirms cloud provider usage even when the company doesn't publicise it. Useful for understanding infrastructure investment, compliance posture (some industries require specific cloud certifications), and technical architecture.

**How to do it:**
1. Resolve key domains and subdomains to IPs
2. Check against published ranges:
   - AWS: https://ip-ranges.amazonaws.com/ip-ranges.json
   - Azure: https://www.microsoft.com/en-us/download/details.aspx?id=56519
   - GCP: https://www.gstatic.com/ipranges/cloud.json
3. `whois <IP>` will also typically identify the hosting provider in the OrgName field

### Storage Bucket Enumeration

**What it is:** Checking for publicly accessible cloud storage buckets associated with the company.

**Why it matters:** Misconfigured buckets can expose sensitive data, but even properly configured ones reveal cloud usage patterns. Bucket naming conventions often follow patterns: `company-assets`, `company-backups`, `company-uploads`.

**How to do it:**
- Check for S3 patterns: `https://company.s3.amazonaws.com` or `https://s3.amazonaws.com/company`
- Azure Blob: `https://company.blob.core.windows.net`
- GCS: `https://storage.googleapis.com/company`
- Look for bucket references in page source, JavaScript files, and API responses

### HTTP Response Header Fingerprinting

**What it is:** Analysing HTTP response headers to identify the web server, CDN, framework, and other infrastructure components.

**Why it matters:** Headers leak implementation details. The `Server` header identifies web server software. `X-Powered-By` reveals the application framework. CDN-specific headers (e.g., `cf-ray` for Cloudflare, `x-amz-cf-id` for CloudFront) confirm CDN usage. Custom headers may reveal internal tool names.

**How to do it:**
```
curl -I https://company.com
```
Key headers to examine:
| Header | Reveals |
|---|---|
| `Server` | Web server (nginx, Apache, IIS, etc.) |
| `X-Powered-By` | Application framework (Express, PHP, ASP.NET) |
| `cf-ray`, `cf-cache-status` | Cloudflare CDN |
| `x-amz-cf-id`, `x-amz-cf-pop` | AWS CloudFront |
| `x-vercel-id` | Vercel hosting |
| `x-netlify-...` | Netlify |
| `x-cache`, `x-served-by` | Fastly CDN |
| `x-github-request-id` | GitHub Pages |
| `x-shopify-stage` | Shopify |
| `x-wix-...` | Wix |
| `x-squarespace-...` | Squarespace |
| `Set-Cookie` | Session management, analytics tools |

---

## 5. Email Infrastructure Analysis

Email infrastructure reveals communication tools, security posture, and third-party service integrations.

### SPF Record Decoding

**What it is:** Systematically parsing SPF (Sender Policy Framework) records to identify all authorised email-sending services.

**Why it matters:** SPF is a comprehensive inventory of every service the company authorises to send email on their behalf. This includes primary email, marketing automation, transactional email, CRM, helpdesk, and more.

**How to do it:**
```
dig TXT company.com | grep "v=spf1"
```

**Interpretation guide:**
- `include:` — References another domain's SPF record (typically a service provider)
- `a:` — Authorises a specific hostname
- `ip4:` / `ip6:` — Authorises specific IP addresses (possibly on-premises mail servers)
- `mx` — Authorises the domain's MX servers
- `all` qualifier:
  - `-all` (hard fail) — Strict; only listed sources are authorised
  - `~all` (soft fail) — Permissive; unlisted sources are suspicious but not rejected
  - `?all` (neutral) — No policy; SPF is informational only
  - `+all` (pass all) — Dangerous misconfiguration; anyone can spoof

If SPF has nested `include:` statements, recursively resolve them:
```
dig TXT _spf.google.com
```

### DMARC Record Analysis

**What it is:** DMARC (Domain-based Message Authentication, Reporting, and Conformance) records specify how receiving mail servers should handle messages that fail SPF/DKIM checks.

**Why it matters:** DMARC policy strength indicates email security maturity:
- `p=none` — Monitoring only; no enforcement (early stage or low priority)
- `p=quarantine` — Failing messages go to spam (intermediate)
- `p=reject` — Failing messages are dropped (mature security posture)

**How to do it:**
```
dig TXT _dmarc.company.com
```
Key fields:
- `p=` — Policy (none/quarantine/reject)
- `rua=` — Aggregate report recipients (sometimes reveals security vendor)
- `ruf=` — Forensic report recipients
- `pct=` — Percentage of messages subject to policy (100 = full enforcement)
- `sp=` — Subdomain policy

### DKIM Selector Identification

**What it is:** DKIM (DomainKeys Identified Mail) uses public/private key pairs to sign emails. The public key is published in DNS under a selector name.

**Why it matters:** DKIM selectors often follow naming conventions that reveal the sending service (e.g., `google`, `selector1` for Microsoft, `s1` for generic, `k1` for Mailchimp).

**How to do it:**
```
dig TXT google._domainkey.company.com
dig TXT selector1._domainkey.company.com
dig TXT selector2._domainkey.company.com
dig TXT k1._domainkey.company.com
dig TXT s1._domainkey.company.com
dig TXT mandrill._domainkey.company.com
dig TXT smtp._domainkey.company.com
```

### Email Address Pattern Discovery

**What it is:** Determining the email address format used by the company (e.g., first.last@, firstl@, first@).

**Why it matters:** Knowing the pattern allows construction of email addresses for any known employee. The pattern also reveals organisational conventions and sometimes legacy vs acquired naming.

**How to do it:**
- Check press releases and media contacts for published email addresses
- Examine PDF metadata (Author field sometimes contains email)
- Review WHOIS registrant email
- Check the website's contact page source code
- Look at job postings for recruiter contact details
- Hunter.io: https://hunter.io/ — indexes publicly available email addresses by domain
- EmailFormat.com: https://www.email-format.com/ — crowdsourced format data
- Search GitHub commits by company domain for developer emails

---

## 6. Document and Image Metadata Extraction

Files published on websites contain embedded metadata that was often not intended for public consumption.

### PDF Metadata

**What it is:** PDF files contain structured metadata fields that record information about the document's creation environment.

**Why it matters:** PDF metadata frequently reveals internal author names (often full names not listed on the website), the software used to create the document (indicating internal tooling), creation and modification timestamps, and sometimes internal file paths or printer names.

**How to do it:**
```
exiftool document.pdf
```
Key fields:
- **Author**: Person who created the document (may differ from attributed author)
- **Creator**: Application used to create (e.g., "Microsoft Word", "Adobe InDesign", "Canva")
- **Producer**: PDF rendering engine (e.g., "macOS Quartz", "Adobe PDF Library", "wkhtmltopdf")
- **CreateDate / ModifyDate**: When the document was created and last modified
- **Custom Metadata**: Some organisations embed custom fields
- **Embedded Fonts**: Font licensing can indicate design tools and budget
- **Keywords**: Sometimes populated with internal tags

### Image EXIF Data

**What it is:** EXIF (Exchangeable Image File Format) data embedded in photographs by cameras and image editing software.

**Why it matters:** EXIF data can contain GPS coordinates (office location verification), camera model (professional vs phone photos), timestamps (event dating), and software used for editing.

**How to do it:**
```
exiftool image.jpg
```
Key fields:
- **GPS Latitude/Longitude**: Physical location where the photo was taken
- **Make/Model**: Camera or phone model
- **DateTimeOriginal**: When the photo was taken
- **Software**: Editing software used (Photoshop, Lightroom, Snapseed)
- **Copyright**: Sometimes contains photographer or company name

### Office Document Metadata

**What it is:** Microsoft Office and Google Docs files embed metadata about authorship, editing history, and the organisation.

**Why it matters:** The "Company" field in Office documents often contains the licensed organisation name. "Last Modified By" reveals collaborators. "Revision count" and "Total editing time" indicate how much work went into the document. Internal file paths embedded in linked objects can reveal server names and directory structures.

**How to do it:**
```
exiftool document.docx
```
Key fields:
- **Author / Creator**: Document creator
- **Last Modified By / LastSavedBy**: Most recent editor
- **Company**: Organisation name from Office license
- **Manager**: Sometimes populated in enterprise environments
- **Revision Number**: How many times the document was saved
- **Total Edit Time**: Cumulative editing duration
- **Template**: Document template used (may reveal internal template systems)
- **Application**: Exact software version

### Practical Metadata Workflow

1. Crawl the company website for all downloadable files (PDFs, DOCX, XLSX, PPTX, images)
2. Download all files
3. Run `exiftool` across all files: `exiftool -r -csv /path/to/downloads/ > metadata.csv`
4. Cross-reference extracted author names with the known people list
5. Look for names NOT on the public team page — these may be departed employees, contractors, or internal staff
6. Note software versions and creation dates for technology and timeline intelligence

---

## 7. Reverse Image Search

Using images found on a company's website to discover additional context, verify authenticity, and trace origins.

### Google Images Reverse Search

**What it is:** Uploading an image to Google Images to find where else it appears online.

**Why it matters:** Discovers if the same image is used on other websites (stock photos on team pages), finds higher-resolution versions, and locates the original source of images used by the company.

**How to do it:**
1. Go to https://images.google.com
2. Click the camera icon
3. Upload the image or paste the image URL
4. Review results for other sites using the same image

### TinEye

**What it is:** A dedicated reverse image search engine that specialises in finding the earliest known instance of an image online.

**Why it matters:** TinEye's "Oldest" sort order reveals where an image first appeared. If a "team photo" first appeared on a stock photo site years before the company existed, it is a stock photo being passed off as genuine.

**How to do it:**
1. Go to https://tineye.com
2. Upload image or paste URL
3. Sort by "Oldest" to find the original source
4. Sort by "Best Match" for the highest quality version

### Yandex Images

**What it is:** The Russian search engine Yandex has image search capabilities that often outperform Google for facial recognition and matching.

**Why it matters:** Yandex frequently returns more accurate results for face-based searches than Google or TinEye. Particularly useful for verifying whether team member photos are stock photos or belong to the claimed person.

**How to do it:**
1. Go to https://yandex.com/images/
2. Click the camera icon
3. Upload image
4. Review results — pay attention to face matches

### Applications

- **Fake team members**: Upload team headshots to detect stock photos. A "Chief Technology Officer" whose photo is available on Shutterstock is a red flag.
- **Office verification**: Reverse search office photos to verify they are genuine and not stock images of co-working spaces.
- **Logo tracing**: Find the earliest appearance of a company logo to verify founding date claims.
- **Product origin verification**: Check if product images are original or sourced from manufacturers/competitors.
- **Event verification**: Confirm that photos of claimed events, offices, or locations are genuine.

---

## 8. Wayback Machine Advanced Techniques

The Internet Archive's Wayback Machine is an invaluable resource for historical intelligence, revealing how a company has changed its messaging, team, services, and claims over time.

### CDX API — Full URL Inventory

**What it is:** The CDX (Capture/Digital Index) API provides programmatic access to all URLs archived for a domain, with metadata including timestamps, HTTP status codes, and MIME types.

**Why it matters:** The CDX API reveals every page the Wayback Machine has ever captured for a domain — including pages that no longer exist, internal paths that were briefly exposed, and the full historical structure of the website.

**How to do it:**
```
http://web.archive.org/cdx/search/cdx?url=company.com/*&output=text&fl=timestamp,original,statuscode&collapse=urlkey
```
Parameters:
- `url=company.com/*` — All URLs under the domain
- `output=text` — Plain text output (also supports `json`)
- `fl=timestamp,original,statuscode` — Fields to return
- `collapse=urlkey` — Deduplicate by URL (one result per unique URL)
- `limit=1000` — Limit results (remove for complete data)
- `from=20200101&to=20231231` — Date range filter

### Deleted Page Recovery

**What it is:** Accessing archived versions of pages that now return 404 errors.

**Why it matters:** Companies delete pages for reasons — removed team members, discontinued services, retracted claims, resolved controversies. The deleted content is often the most interesting content.

**How to do it:**
1. Use CDX API to find URLs that previously returned 200 but now return 404
2. Access the archived version: `https://web.archive.org/web/YYYYMMDD/https://company.com/deleted-page`
3. Compare the last available version with current site structure

### robots.txt History

**What it is:** Tracking changes to a company's robots.txt file over time via the Wayback Machine.

**Why it matters:** robots.txt tells search engines which paths to avoid. Companies progressively add paths to robots.txt when they want to hide content from search engines. A newly blocked path suggests something the company wants to suppress. Historical robots.txt snapshots reveal this progression.

**How to do it:**
```
https://web.archive.org/web/*/company.com/robots.txt
```
Diff successive versions to identify newly blocked paths, then check if those paths are archived.

### Snapshot Diffing

**What it is:** Comparing archived snapshots of key pages across different dates.

**Why it matters:** Reveals when and how companies changed their messaging, added or removed team members, adjusted service descriptions, modified client lists, or altered claims. Particularly powerful for:
- **About page**: Mission/vision evolution, founding narrative changes
- **Team page**: Staff turnover, role changes, added/removed positions
- **Services page**: Pivots, new offerings, discontinued services
- **Client/partner pages**: Relationships gained and lost

**How to do it:**
1. Navigate to `https://web.archive.org/web/*/company.com/about`
2. Select two snapshots from different dates
3. Use the "Changes" feature or manually compare content
4. For systematic analysis, download both versions and use a diff tool

### Archived Sitemaps

**What it is:** Retrieving historical sitemap.xml files from the Wayback Machine.

**Why it matters:** Sitemaps provide a structured inventory of all pages the company considered important enough to include. Comparing historical sitemaps reveals structural changes to the website over time.

**How to do it:**
```
https://web.archive.org/web/*/company.com/sitemap.xml
```

### Alternative Archives

When the Wayback Machine lacks coverage, try:
- **archive.today** (also archive.is, archive.ph): User-submitted snapshots, often captures pages the Wayback Machine misses
- **CachedView** (cachedview.nl): Aggregates cached versions from multiple sources
- **Google Cache**: `cache:company.com/page` in Google search (ephemeral, only most recent)
- **Common Crawl**: https://commoncrawl.org/ — Monthly web crawls with raw HTML available for download

---

## 9. Google Dork Reference for Company Research

Google dorking uses advanced search operators to find specific content that standard searches miss. Below is a comprehensive reference organised by research objective.

### Site-Restricted File and Path Discovery

```
site:company.com filetype:pdf
site:company.com filetype:xlsx
site:company.com filetype:docx
site:company.com filetype:pptx
site:company.com filetype:csv
site:company.com filetype:xml
site:company.com filetype:json
site:company.com inurl:admin
site:company.com inurl:login
site:company.com inurl:dashboard
site:company.com inurl:portal
site:company.com inurl:internal
site:company.com inurl:staging
site:company.com inurl:test
site:company.com inurl:api
site:company.com inurl:wp-content          (WordPress indicator)
site:company.com inurl:wp-admin            (WordPress admin)
site:company.com ext:env                    (Environment files)
site:company.com ext:log                    (Log files)
site:company.com ext:sql                    (Database dumps)
site:company.com ext:bak                    (Backup files)
```

### Finding the Company on Third-Party Sites

```
site:linkedin.com "Company Name"
site:linkedin.com/company "Company Name"
site:linkedin.com/in "Company Name"         (employee profiles)
site:glassdoor.com.au "Company Name"
site:seek.com.au "Company Name"
site:indeed.com.au "Company Name"
site:reddit.com "Company Name"
site:whirlpool.net.au "Company Name"
site:github.com "Company Name"
site:medium.com "Company Name"
site:youtube.com "Company Name"
site:twitter.com "Company Name"
site:facebook.com "Company Name"
site:crunchbase.com "Company Name"
site:producthunt.com "Company Name"
site:trustpilot.com "Company Name"
site:g2.com "Company Name"
site:capterra.com "Company Name"
```

### Government and Official Sources (Australian)

```
site:austlii.edu.au "Company Name"          (legal cases)
site:aph.gov.au "Company Name"              (parliamentary records)
site:tenders.gov.au "Company Name"           (government tenders)
site:grants.gov.au "Company Name"            (government grants)
site:abr.business.gov.au "Company Name"      (ABN Lookup)
site:asic.gov.au "Company Name"              (corporate regulator)
site:acnc.gov.au "Company Name"              (charity register)
site:data.gov.au "Company Name"              (open government data)
site:trove.nla.gov.au "Company Name"         (historical newspapers/records)
site:ipaustralia.gov.au "Company Name"       (trademarks/patents)
site:austrac.gov.au "Company Name"           (financial intelligence)
site:oaic.gov.au "Company Name"              (privacy breaches)
site:cyber.gov.au "Company Name"             (cybersecurity incidents)
site:ato.gov.au "Company Name"               (tax rulings involving company)
```

### Date-Bounded Searches

```
"Company Name" after:2024-01-01 before:2024-12-31
"Company Name" after:2023-06-01              (everything since a date)
"Company Name" "2024 annual report"
"Company Name" funding OR investment after:2023-01-01
```

### Finding Related Entities

```
"Company Name" partner OR partnership
"Company Name" client OR customer
"Company Name" funding OR investment OR raised
"Company Name" acquisition OR acquired OR merger
"Company Name" lawsuit OR litigation OR "court"
"Company Name" "signed" OR "agreement" OR "contract"
"Company Name" subcontractor OR supplier OR vendor
"Company Name" sponsor OR sponsorship
"Company Name" MOU OR "memorandum of understanding"
```

### Person-Specific Searches

```
"Person Name" "Company Name"
"Person Name" site:linkedin.com
"Person Name" site:linkedin.com/in
"Person Name" before:2020-01-01              (pre-company history)
"Person Name" CEO OR founder OR director
"Person Name" resume OR CV filetype:pdf
"Person Name" speaker OR conference OR panel
"Person Name" "board of directors" OR "advisory board"
```

### Negative and Controversial Coverage

```
"Company Name" scandal OR controversy OR investigation
"Company Name" complaint OR "rip off" OR scam
"Company Name" breach OR hack OR leak
"Company Name" lawsuit OR sued OR plaintiff OR defendant
"Company Name" terminated OR fired OR redundancy
"Company Name" review -site:company.com       (external reviews)
"Company Name" "fair work" OR "unfair dismissal"
"Company Name" ACCC OR "consumer protection"
"Company Name" insolvent OR liquidation OR "voluntary administration"
"Company Name" fine OR penalty OR sanction
```

### Competitive Intelligence

```
"Company Name" vs OR versus OR alternative OR competitor
"Company Name" comparison OR compare
"Company Name" market share OR "industry report"
"Company Name" OR "Competitor Name" filetype:pdf
related:company.com                          (Google's related sites)
```

### Finding Hidden Content

```
related:company.com                          (sites Google considers similar)
link:company.com                             (pages linking to the company)
inanchor:"Company Name"                      (pages with company name in link text)
allinurl:company keyword                     (URL containing both terms)
"Company Name" -site:company.com -site:linkedin.com -site:facebook.com
                                             (strip common sites for deep results)
```

---

## 10. Web Application Fingerprinting

Analysing the company's web application to identify technology choices, development practices, and potential intelligence signals hidden in the frontend.

### HTTP Response Headers

See Section 4 (HTTP Response Header Fingerprinting) for the core technique. Additionally check:
- `X-Frame-Options` — Security header presence indicates security awareness
- `Content-Security-Policy` — CSP headers reveal allowed third-party domains
- `Strict-Transport-Security` — HSTS indicates HTTPS enforcement maturity
- `X-Content-Type-Options`, `X-XSS-Protection` — Security header hygiene

### robots.txt Analysis

**What it is:** The robots.txt file tells search engine crawlers which paths to avoid.

**Why it matters:** Blocked paths are intelligence. If `/admin`, `/internal`, `/staging`, or `/api/v2` are blocked, those paths exist. robots.txt is a roadmap of what the company wants to keep out of search engines.

**How to do it:**
```
https://company.com/robots.txt
```
Look for:
- Admin panels and internal tools
- API endpoints and documentation
- Staging or development paths
- User-generated content paths
- Paths that suggest specific CMS or framework usage

### security.txt and humans.txt

**What it is:** Standardised files that provide security contact information and team credits respectively.

**Why it matters:** `security.txt` (at `/.well-known/security.txt`) reveals the security contact, preferred communication method, and sometimes a PGP key — indicating security program maturity. `humans.txt` sometimes lists team members, agencies, and tools used.

**How to do it:**
```
https://company.com/.well-known/security.txt
https://company.com/humans.txt
```

### Error Page Fingerprinting

**What it is:** Examining error pages (404, 500, 403) for technology stack information.

**Why it matters:** Default error pages often reveal the web server, framework, or hosting platform. Custom error pages may still leak version information or internal naming.

**How to do it:**
Visit a non-existent URL like `https://company.com/thispagedoesnotexist` and examine the error page for:
- Framework default error pages (Rails, Django, Express, Laravel)
- Server version information
- Hosting platform branding
- Debug information left enabled in production

### Source Code Analysis

**What it is:** Examining the HTML source, JavaScript, and embedded metadata of the company's web pages.

**Why it matters:** Source code contains numerous intelligence signals that are not visible in the rendered page.

**How to do it:**

**Google Analytics ID reverse lookup:**
- Find the GA tracking ID in the source (`UA-XXXXXXX-X` or `G-XXXXXXXXXX`)
- Use tools like BuiltWith or SpyOnWeb to find all websites sharing the same GA ID
- Shared GA IDs indicate common ownership across multiple domains

**Google Tag Manager containers:**
- Find the GTM container ID (`GTM-XXXXXXX`) in the source
- GTM containers may be publicly viewable and reveal all tags/triggers configured
- Tags reveal analytics, advertising, and third-party integrations

**Tracking pixels and third-party scripts:**
- Facebook Pixel (`fbq('init', 'XXXXXXXXXX')`) — Facebook advertising
- LinkedIn Insight Tag — LinkedIn advertising
- HubSpot tracking code — HubSpot CRM/marketing
- Intercom — Customer messaging platform
- Drift, Crisp, LiveChat — Chat widgets reveal customer support tools
- Hotjar, FullStory, Crazy Egg — Session recording/heatmap tools
- Segment — Customer data platform (indicates sophisticated data stack)
- Mixpanel, Amplitude — Product analytics (indicates product-led growth)

**Meta tags:**
- `<meta name="generator">` — CMS identification (WordPress, Drupal, Squarespace)
- `<meta name="author">` — Page author
- Open Graph and Twitter Card meta tags — Social media presentation choices

**Developer comments:**
- HTML comments (`<!-- -->`) sometimes contain TODO items, developer names, internal references, or debug notes
- JavaScript comments may reference internal APIs, staging URLs, or team members

**Source maps (.map files):**
- Check for `.map` files (e.g., `main.js.map`) which contain the original unminified source code
- Source maps may reveal the full project structure, variable names, and internal logic
- Check by appending `.map` to JavaScript file URLs

---

## 11. Code Repository Intelligence

Public code repositories are a rich source of intelligence about a company's technical capabilities, team composition, and operational practices.

### GitHub/GitLab/Bitbucket Searches

**What it is:** Searching public code hosting platforms for repositories and contributions associated with the company and its employees.

**Why it matters:** Public repositories reveal the company's technology stack, coding standards, team size and activity, open-source contributions, and sometimes accidentally committed sensitive information.

**How to do it:**

**Company organisation search:**
```
https://github.com/companyname
https://github.com/orgs/companyname/repositories
```

**GitHub code search for the company:**
```
https://github.com/search?q="company.com"&type=code
https://github.com/search?q=org:companyname&type=repositories
```

**Employee discovery via commits:**
```
https://github.com/search?q="@company.com"&type=commits
```

### What Repositories Reveal

- **Technology stack**: Languages, frameworks, libraries, and tools used
- **Team size and activity**: Number of contributors, commit frequency, active vs dormant repos
- **Code quality**: Code review practices, testing coverage, documentation quality
- **Accidentally committed secrets**: API keys, passwords, internal URLs (search commit history, not just current state)
- **Internal tool names**: References to internal systems in README files or code comments
- **Architecture decisions**: Microservices vs monolith, database choices, infrastructure-as-code patterns
- **Hiring signals**: "We're hiring" in READMEs, contributor growth trends

### Package Registries

**What it is:** Checking public package registries for packages published by the company.

**Why it matters:** Published packages confirm technology stack choices and sometimes reveal internal tooling that has been open-sourced. Package metadata includes maintainer information and sometimes links to private repositories.

**How to do it:**
- **npm** (JavaScript): `https://www.npmjs.com/~companyname` or search for the company name
- **PyPI** (Python): `https://pypi.org/search/?q=companyname`
- **RubyGems** (Ruby): `https://rubygems.org/search?query=companyname`
- **Maven Central** (Java): Search for the company's group ID
- **NuGet** (.NET): `https://www.nuget.org/profiles/companyname`
- **Docker Hub**: `https://hub.docker.com/u/companyname`

---

## 12. Advertising Intelligence

Publicly accessible advertising libraries reveal a company's marketing strategy, messaging, target audiences, and budget allocation.

### Google Ads Transparency Center

**What it is:** Google's public repository of all ads run through Google Ads, searchable by advertiser name.

**Why it matters:** Reveals active advertising campaigns, ad creative/messaging, geographic targeting, and the duration ads have been running. Indicates marketing budget allocation and strategic priorities.

**How to do it:**
```
https://adstransparency.google.com/?region=AU
```
Search for the company name. Review:
- Active vs recently ended ads
- Ad formats (search, display, video, shopping)
- Messaging themes and value propositions
- Geographic targeting
- Date ranges (campaign duration)

### Meta Ad Library (Facebook/Instagram)

**What it is:** Meta's public archive of all active and recently inactive ads on Facebook and Instagram.

**Why it matters:** All active Meta ads are publicly viewable regardless of whether you are in the target audience. This reveals messaging, creative assets, A/B testing variations, and special category ads (housing, employment, social issues, politics).

**How to do it:**
```
https://www.facebook.com/ads/library/?active_status=all&ad_type=all&country=AU&q=Company%20Name
```
Review:
- Number of active ads (indicates marketing investment)
- Ad creative (images, videos, carousels)
- Ad copy and calls-to-action
- Multiple variations (A/B testing activity)
- "Started running on" dates
- Page name (may differ from company name)
- Special ad categories declared

### LinkedIn Ad Library

**What it is:** LinkedIn's public archive of sponsored content run by company pages.

**Why it matters:** LinkedIn ads are typically B2B focused, revealing the company's professional positioning, thought leadership strategy, recruitment advertising, and target audience (by examining ad content and messaging).

**How to do it:**
- Visit the company's LinkedIn page
- Navigate to the "Posts" tab and filter for "Ads"
- Or search LinkedIn's Ad Library directly

---

## 13. Operational Security Awareness

When conducting OSINT, the researcher leaves their own digital footprint. Understanding these risks allows informed decisions about visibility.

### Web Fetch Attribution Risks

**What it is:** Every time you visit a website, the server logs your IP address, user agent, referrer, and potentially tracks behaviour via analytics.

**Why it matters:** If researching a company's website extensively, their analytics may show unusual traffic patterns — particularly if using web fetch tools that make rapid sequential requests from identifiable IPs or user agents.

**Mitigation:**
- Be aware that visits are logged; this is generally acceptable for professional research
- Avoid rapid-fire requests that look like automated scanning
- Cached content (Wayback Machine, Google Cache) does not alert the target
- Web fetch tools may have identifiable user agent strings

### LinkedIn Profile Viewing

**What it is:** LinkedIn notifies users when someone views their profile (unless the viewer uses "Private mode").

**Why it matters:** If you view a CEO's LinkedIn profile, they may be notified — which could reveal the research activity. This is rarely a practical concern but worth noting for sensitive engagements.

**Mitigation:**
- Use LinkedIn's anonymous browsing mode when available
- Be aware that even in anonymous mode, the user sees "someone from [industry] viewed your profile"
- Public LinkedIn data can often be accessed without logging in, avoiding view notifications entirely
- LinkedIn profile data is frequently cached by search engines

### Social Media Engagement Visibility

**What it is:** Likes, comments, follows, and other engagements on social media platforms are often visible to the target and sometimes publicly.

**Why it matters:** Accidentally liking a post or following an account during research creates a visible connection.

**Mitigation:**
- Use logged-out browsing for social media research where possible
- Do not interact with content (like, comment, share, follow) during research
- Screenshot content rather than bookmarking it on the platform

### General Mitigation Approach

- **Timing**: Spread research across multiple sessions rather than intensive single sessions
- **Caching**: Prefer cached/archived versions of content where available
- **Awareness**: Make an informed choice about what level of visibility is acceptable for the engagement
- **Proportionality**: For most professional research, website visits and public record queries are entirely appropriate and expected

---

## 14. Negative Space Checklist

Analysing what is absent or conspicuously missing is as important as analysing what is present. Absences are often deliberate. This checklist provides a structured approach to identifying significant gaps.

### Website and Marketing Gaps

- [ ] **Sector omissions**: Lists clients across multiple sectors but conspicuously omits one? May indicate a failed engagement or deliberate avoidance.
- [ ] **Team page without photos**: Text-only team listings may indicate a very small team, high turnover, or reluctance to show the actual team.
- [ ] **No team page at all**: Some legitimate companies omit team pages, but combined with other signals this raises questions.
- [ ] **Careers page with no current openings**: May indicate hiring freeze, or the careers page is a template never updated.
- [ ] **Impact claims without metrics**: "We've helped hundreds of organisations" without specific numbers, named clients, or case studies.
- [ ] **Blog that went silent**: Regular blogging that suddenly stopped may indicate resource constraints, a pivot, or internal disruption.
- [ ] **No case studies or testimonials**: Claims expertise but provides no evidence.
- [ ] **No pricing information**: May be standard for the industry, or may indicate custom (inconsistent) pricing.
- [ ] **Missing financial information**: For entities required to report (charities, public companies), absence of financial data is a significant red flag.

### People and Social Gaps

- [ ] **LinkedIn profiles exist but company page is sparse**: Staff maintain personal profiles but the company page has minimal content and few followers.
- [ ] **Key leadership with no LinkedIn presence**: Unusual in professional services; may indicate privacy preference or undisclosed history.
- [ ] **No staff on LinkedIn at all**: Very unusual for a company of any size; may indicate the company is smaller than claimed.
- [ ] **Board members with no other board roles**: For established professionals, a single board seat with no history raises questions.

### Competitive and Market Gaps

- [ ] **Competitors mention them but not vice versa**: Asymmetric awareness may indicate one party is much larger or the relationship is adversarial.
- [ ] **Present in industry directories but missing from key ones**: Selective presence may indicate selective membership or expired memberships.
- [ ] **No media coverage despite claimed prominence**: A company claiming to be a "market leader" with zero media mentions.

### Timeline Gaps

- [ ] **Gap in their timeline**: A company narrative that jumps from "founded in 2010" to "in 2018 we..." — what happened in between?
- [ ] **Wayback Machine gaps**: Periods where the website was down or drastically reduced.
- [ ] **LinkedIn activity gaps**: Periods of no posts or engagement.
- [ ] **Filing gaps**: Missing annual reports, late ASIC filings, or lapsed registrations.

---

## 15. Counter-Deception Detection

Systematic techniques for verifying claims and detecting misrepresentation.

### Employee Count Verification

**What it is:** Cross-referencing stated employee numbers across multiple sources.

**Why it matters:** Companies frequently inflate headcount to appear larger than they are. Discrepancies between sources indicate either rapid change or misrepresentation.

**How to do it:**
Compare numbers across:
- Company website ("Our team of 50+ professionals")
- LinkedIn company page (shows employee count)
- LinkedIn search results for current employees
- ACNC annual reports (for charities; reports paid staff and volunteers separately)
- ASIC annual reports (for companies required to report)
- Job advertisements ("Join our growing team of 30")
- Glassdoor reviews (number of reviews relative to claimed size)

Red flags:
- Website claims 50+ staff but LinkedIn shows 12 people listing the company as employer
- Claimed headcount doubled without visible hiring activity
- High headcount but no office address or small office

### Revenue Claims Cross-Checking

**What it is:** Verifying revenue or financial claims against available data.

**Why it matters:** Revenue claims are used to signal credibility and attract clients, partners, and investors. Unverifiable claims should be flagged.

**How to do it:**
- Check ASIC filings for lodged financial statements (large proprietary companies)
- Check ACNC annual information statements (charities)
- Cross-reference with industry benchmarks (revenue per employee)
- Check awards submissions (sometimes include revenue data)
- Media interviews where founders state figures
- Crunchbase, PitchBook for funding data (funded companies)

### Client Claim Verification

**What it is:** Verifying that claimed client relationships actually exist.

**Why it matters:** Some companies list logos of companies they have never worked with, or inflate the nature of small engagements.

**How to do it:**
- Search for the claimed client mentioning the company (reciprocal reference)
- Check the client's vendor/partner page for reciprocal listing
- Search for case studies or joint press releases
- Check if the company logo appears on the client's supplier registry
- Look for procurement records (government clients)
- Check the timing — did the "client" exist when the work was allegedly done?

### Award Verification

**What it is:** Checking whether claimed awards are legitimate, merit-based recognitions or pay-to-play schemes.

**Why it matters:** The "awards industry" includes numerous pay-to-play schemes where companies pay entry fees and receive awards regardless of merit. Displaying these as genuine achievements is misleading.

**How to do it:**
- Search for the awarding body — is it a recognised industry organisation?
- Check if the award requires a paid entry or nomination fee
- Look at past winners — are they consistently the same companies that can afford entry fees?
- Check if the award has a judging panel of credible, named individuals
- Legitimate awards: industry association awards, government-recognised awards, peer-nominated awards
- Suspicious: "Top 100" lists from obscure publications, awards from organisations whose primary business model is awards

### Partnership Verification

**What it is:** Verifying claimed partnerships and affiliations.

**Why it matters:** Companies may claim partnerships that are actually just vendor relationships, expired arrangements, or aspirational connections.

**How to do it:**
- Check the partner's website for reciprocal acknowledgment
- Verify partnership tier (e.g., "AWS Partner" could mean anything from a free-tier listing to a Premier Consulting Partner)
- Check partnership directories maintained by the larger partner
- Look for partnership expiry (some partnerships require annual renewal)

### Temporal Deception Detection (Wayback Machine)

**What it is:** Using historical website snapshots to detect when claims were added or modified.

**Why it matters:** If a company adds "Est. 2005" to their website in 2020, or adds a client logo to their portfolio years after the alleged engagement, this is temporal deception — backdating claims.

**How to do it:**
1. Identify key claims on the current website (founding date, client list, team size, services)
2. Find the earliest Wayback Machine snapshot containing each claim
3. Compare the claim's appearance date with the claimed timeframe
4. Flag discrepancies (e.g., "10 years of experience" first appearing on a 2-year-old website)

### Stock Photo Detection on Team Pages

**What it is:** Checking whether team member photos are stock photography rather than genuine photos.

**Why it matters:** Using stock photos for team members is a significant deception — it means those people either do not exist or the company does not want to show who they actually are.

**How to do it:**
1. Save each team member photo
2. Run through reverse image search (TinEye, Google Images, Yandex)
3. Check for stock photo watermarks, unnaturally perfect lighting, or generic backgrounds
4. Cross-reference with LinkedIn profiles — does the same person with the same photo exist on LinkedIn?
5. AI-generated faces: look for asymmetric earrings, blurred backgrounds merging with hair, inconsistent teeth

---

## 16. Query Iteration Strategy

A structured methodology for progressively refining searches to extract maximum information while minimising noise.

### Step 1: Start Broad

Begin with the company name in quotes to establish baseline coverage.
```
"Company Name"
```
Assess: How many results? What sources appear? What is the general sentiment?

### Step 2: Add Context Qualifiers

Narrow by adding relevant context terms.
```
"Company Name" Australia
"Company Name" Melbourne consulting
"Company Name" CEO founder
"Company Name" annual report 2024
```
Each qualifier focuses the results on a specific dimension of the company.

### Step 3: Subtract Noise

Remove dominant but unhelpful results.
```
"Company Name" -site:company.com -site:linkedin.com -site:facebook.com
"Company Name" -jobs -careers -hiring
"Company Name" -"press release" -"media release"
```
Subtracting the company's own site and social profiles surfaces third-party coverage.

### Step 4: Exact Match for Specific Claims

When verifying a specific claim, search for it exactly as stated.
```
"Company Name" "awarded contract" "Department of Health"
"Company Name" "Series B" "$10 million"
"Person Name" "PhD" "University of Melbourne"
```
Exact matches either confirm or fail to find evidence for specific claims.

### Step 5: OR for Variant Names

Companies may be known by multiple names, abbreviations, or former names.
```
"Company Name" OR "Company Pty Ltd" OR "Company Group" OR "Former Name"
"CompanyName" OR "Company Name" OR "Company_Name"
```
Ensure all name variants are captured.

### Step 6: Exhaust Date Ranges

Systematically search across time periods to ensure comprehensive coverage.
```
"Company Name" after:2020-01-01 before:2020-12-31
"Company Name" after:2021-01-01 before:2021-12-31
"Company Name" after:2022-01-01 before:2022-12-31
"Company Name" after:2023-01-01 before:2023-12-31
"Company Name" after:2024-01-01 before:2024-12-31
"Company Name" after:2025-01-01
```
Annualised searching prevents newer results from drowning out older, potentially more revealing content.

### Step 7: Search in Different Languages

If the company operates internationally or has roots in non-English-speaking markets, search in relevant languages.
```
"Company Name" site:.de            (German sites)
"Company Name" site:.jp            (Japanese sites)
"会社名"                            (Company name in Japanese)
```
Non-English sources may contain coverage absent from English-language results, particularly for companies with international operations, supply chains, or ownership structures.

### Iteration Principles

- **Patience over speed**: Thorough iteration across multiple query variations yields more than a single well-crafted search.
- **Record everything**: Log each query and its result count to track coverage and avoid repetition.
- **Follow threads**: When a result mentions a new entity, person, or event, immediately search for that new term.
- **Revisit with new knowledge**: After completing initial research, return to search with newly discovered names, dates, and entities as search terms.
- **Combine techniques**: Use Google dorks, site-specific searches, and date ranges together for maximum precision.

---

## 17. Social Media OSINT

Social media platforms are high-value OSINT sources for company research — they reveal culture, leadership style, customer sentiment, hiring signals, and product direction. Access constraints vary significantly by platform.

### LinkedIn

**What to look for:**
- Company page: employee count trend (growing or shrinking?), recent posts, product/service descriptions
- Individual profiles: leadership team career histories, tenure patterns, recent departures
- Job postings: hiring signals about strategic direction, technology stack, geographic expansion

**Access notes:**
- Company pages: WebFetch works for basic info; deeper data requires Layer 3 or Layer 4
- Individual profiles: Layer 4 (Playwright) required — see `layer-4-playwright-protocol.md` for the LinkedIn-specific protocol
- LinkedIn profile views notify the profile owner — inform the user before viewing
- Employee count on the company page is rounded and updated by LinkedIn; treat as ±10% estimate

**Hiring signal interpretation:**
| Signal | Interpretation |
|---|---|
| Multiple senior hires in new geography | Likely expansion into that market |
| Multiple hires in finance/legal roles | Preparing for capital raise, acquisition, or regulatory action |
| Engineering hires with specific tech stack | Platform migration or new product build |
| No hiring activity for 6+ months | Possible freeze — check against financial signals |
| Unusually high role turnover in one function | Cultural or leadership issue in that function |

---

### Twitter / X

**What to look for:**
- Official company account: messaging consistency, response to criticism, engagement quality
- Founder/CEO personal account: unfiltered views, culture signals, investor relationships
- Employee accounts: internal culture, pride or frustration signals
- Mentions and replies: customer complaints, industry peer commentary

**Access:** WebSearch `site:twitter.com "[company name]"` for indexed tweets. WebFetch of profile pages returns limited content — use Layer 3 for JS-rendered tweet content if needed.

**Caution:** Twitter/X content is not archived reliably. Deleted tweets are gone. Screenshots in media reporting are the most durable record of controversial posts.

---

### YouTube

**What to look for:**
- Official channel: product demos, culture videos, conference presentations
- Appearances on other channels: founder/CEO interviews, conference talks, podcasts with video
- Comments: customer and competitor reactions

**Access:** WebFetch and WebSearch work well for YouTube. `site:youtube.com "[company name]"` returns indexed videos.

**High-value pattern:** Conference presentation videos from 2+ years ago often contain strategic commitments that can be compared against what actually happened.

---

### Facebook / Meta Ad Library

**What to look for:**
- Active advertising: are they spending on ads? What products/services are being promoted?
- Ad creative: messaging, target audience signals, offer type (B2C vs B2B signals)
- Ad volume and duration: high spend over long period = healthy marketing budget; sudden drop = budget cuts

**Access:**
- Meta Ad Library is publicly accessible: `https://www.facebook.com/ads/library/?active_status=all&ad_type=all&country=AU&q=[company+name]`
- WebFetch is blocked for facebook.com at the Claude Code network level — use Layer 3 (ScrapingBee with render_js=true) or Layer 4 (Playwright)
- If Layer 3/4 are unavailable, log as manual review item with the URL above

**Interpreting ad absence:** No ads in the Meta Ad Library does not mean the company isn't advertising — it may mean they advertise only on Google, LinkedIn, or industry-specific platforms.

---

### Platform access summary

| Platform | Layer 1 (API) | Layer 2 (WebFetch) | Layer 3 (ScrapingBee) | Layer 4 (Playwright) |
|---|---|---|---|---|
| LinkedIn company page | No | Partial | Yes (render_js=true) | Yes |
| LinkedIn individual profile | No | No | Partial | Yes (preferred) |
| Twitter/X profile | No | Partial | Yes | Yes |
| YouTube | No | Yes | Not needed | Not needed |
| Facebook Ad Library | No | Blocked | Yes (render_js=true) | Yes |

Log all failed access attempts in `inaccessible-sources.md`.
