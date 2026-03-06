GRC Concepts & Compliance Notes

Documenting random governance, risk, and compliance related topics as I encounter them through coursework, research, and the real world.

- - -

## Mutual Legal Assistance Treaties (MLATs)

**Real-world example:**
US law enforcement used the MLAT with Switzerland to make Swiss-based Proton Mail hand over account metadata (credit card number) for a criminal investigation. Proton complied because they are legally required to follow Swiss court orders. Important distinction people are missing: Proton's end-to-end encryption meant they could not hand over email content or file contents (which they should not have access to anyway), only metadata which to my knowledge can't be encrypted, only hidden like in onion routing. Despite backlash, the Proton critique is moot because their job is to encrypt CONTENT. Account creation and payment info are not content. The user's OPSEC failure was using a personal credit card and public IP without a VPN which made them traceable.

**What is an MLAT:**
An agreement between two or more countries that allows them to request and share evidence and information for criminal investigations.

**What can be requested:**
- Witness testimony and statements
- Documents, records, and evidence
- Search and seizure execution
- Locating or identifying people

**Key points:**
- Only available to government officials, usually prosecuters — not private citizens or civil cases
- Requests must go through formal legal processes and be approved by a court in receiving country
- The US has MLATs with 65+ countries including Switzerland, the UK, and all EU member states for starters

**Why it matters for GRC:**
Organizations operating internationally need to understand that legal obligations cross borders. Privacy tools protect content, but metadata and account information can still be captured legally. Compliance teams should consider how MLATs affect who can legally access data and where.

- - - 

## Encryption vs. Metadata

**Real-world (rabbit hole) examples:**
- 2021: Proton handed over IP address and browser fingerprint of a climate activist to Swiss police when requested through Europol. User didn't use a VPN though.
- 2024: Proton handed over a recovery email which was an iCloud email address (metadata and not required by Proton) of a person to Spanish police. Apple then provided full name, home addresses, and linked Gmail.

**So what IS encrypted? Content:**
- Email text and attachments
- Files stored in encrypted drives
- Calendars, notes, etc.
- End to end meaning even the provider can't read it

**What's NOT encrypted? Metadata:**
- IP addresses used to log in
- Account creation date
- Recovery email addresses
- Payment method used
- Email timestamps and recipient addresses(!)
- Device/browser fingerprint (isn't unique 1/1 but can narrow down a search)

**Why it matters for GRC:**
It seems people assume that "encrypted" means invisible. Encryption protects content which really is resting data and data in transit, not the fact that you exist as a user who accessed a service. Metadata alone can be enough to identify somebody. Metadata protection is our responsibility as a user through VPN, anonmyous payment, no recovery acct, etc. If you have shit OPSEC it doesn't matter what company you use, your privacy will never be protected.

- - -

## Swiss Surveillance Law (VÜPF)

**Real-world example**
Switzerland built its reputation as a kind of privacy refuge. Swiss law historically categorized VPN providers differently from telecom providers so VPNs had no logging obligations which is why companies like Proton based themselves there.

**What's changing:**
Switzerland is proposing a revision to the VÜPF that would begin in late 2026:
- Require VPN and email providers to log IP addresses for 6 months
- Mandate user ID verification (official ID or phone number)
- Wants to create backdoor to decrypt data

**Why it matters:**
- Seems this would make Swiss surveillance stricter than the US or EU because it doesn't affect US-based Gmail or WhatsApp for example

**Proton's response:**
- Started moving physical infrastructure to Germany and Norway (EU courts have ruled blanket data retention illegal)
- Proton has already moved new-ish Lumo AI chatbot which is hosted Germany
- Headquarters remain in Geneva, not complete relocation
- CEO Andy Yen said "If necessary, we can shut down the systems in Switzerland within a short period of time"

**Why it matters for GRC:**
A country's privacy laws today don't guarantee its privacy laws tomorrow. Organizations must monitor these changes constantly and have contingency plans.
