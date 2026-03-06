GRC Concepts & Compliance Notes

Documenting random governance, risk, and compliance related topics as I encounter them through coursework, research, and the real world.

- - -

## Mutual Legal Assistance Treaties (MLATs)

**Real-world example:**
US law enforcement used the MLAT with Switzerland to make Swiss-based Proton Mail hand over account metadata (credit card number) for a criminal investigation. Proton complied because they are legally required to follow Swiss court orders. Important distinction people are missing: Proton's end-to-end encryption meant they could not hand over email content or file contents (which they should not have access to anyway), only metadata. Despite backlash, the Proton critique is moot because their job is to encrypt CONTENT. Account creation and payment info are not content. The user's OPSEC failure was using a personal credit card and public IP without a VPN which made them traceable.

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


**Why it matters:**
Organizations operating internationally need to understand that legal obligations cross borders. Privacy tools protect content, but metadata and account information can still be captured legally. Compliance teams should consider how MLATs affect who can legally access data and where.
