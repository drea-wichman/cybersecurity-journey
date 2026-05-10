# GRC Rabbit Hole Notes

Ongoing notes on governance, risk, and compliance topics I chase down for fun. Entries are driven by whatever I'm curious about, reading, or watching in the news, not a set curriculum.

Each entry is dated. Content reflects my understanding at the time of writing and may go out of date as laws, cases, or policies evolve.

*Some are sharp. All are sourced.*

## Contents

- [The Computer Fraud and Abuse Act (CFAA)](#the-computer-fraud-and-abuse-act-cfaa)
- [Executive Order 12333](#executive-order-12333)
- [The Wyden Letter](#the-wyden-letter)
- [Section 702 FISA](#section-702-fisa)
- [Swiss Surveillance Law (VÜPF)](#swiss-surveillance-law-vüpf)
- [Encryption vs. Metadata](#encryption-vs-metadata)
- [Mutual Legal Assistance Treaties (MLATs)](#mutual-legal-assistance-treaties-mlats)

---

## The Computer Fraud and Abuse Act (CFAA)
*Added May 9, 2026*

**Real-world example:**
On May 12, 2017, a ransomware worm called WannaCry was tearing through 150 countries and crippling the UK's National Health Service among many other victims. A 22-year-old British researcher named Marcus Hutchins was reverse engineering a sample from his bedroom when he noticed the malware was making a query to an unregistered domain before executing. He registered the domain for $10.69 which triggered a kill switch that had been built into the code and stopped the attack from spreading further. Within hours, WannaCry was contained and affected computers began recovering. He worked with the UK's National Cyber Security Centre and his US-based employer Kryptos Logic over the following days to keep the kill switch domain online and prevent a second wave. He was widely regarded as the hacker who saved the internet.

Three months later, the FBI arrested him at the Las Vegas airport as he was leaving DEFCON to fly home to the UK. The charges had nothing to do with WannaCry. The US Department of Justice indicted him on ten counts under the Computer Fraud and Abuse Act and the Wiretap Act related to creating, advertising, and selling Kronos, a banking trojan he had worked on years earlier as a teenager, and a related piece of malware called UPAS Kit. Kronos was sold by an unidentified co-conspirator known online as "Vinny" on dark web forums and was used by criminals to steal banking credentials from victims primarily in the UK and India and later spreading globally. Hutchins spent over a year on bail in Los Angeles before pleading guilty to two counts and receiving time served. The other eight counts were dropped.

**What the CFAA is:**
The Computer Fraud and Abuse Act is a US federal law passed in 1986. It is the central statute the US uses to prosecute computer crime, criminalizing unauthorized access to a computer, transmitting code with intent to damage a protected computer, password trafficking, and computer-related fraud. The CFAA defines a "protected computer" as any computer used in or affecting interstate or foreign commerce, which courts have interpreted to cover essentially any computer connected to the internet.
The CFAA does not criminalize writing malware. Creating malicious code is protected speech in the US. Selling and distributing malware to people you know will use it for crimes is criminal under 18 U.S.C. § 2512 which prohibits the manufacture, distribution, and advertising of devices "primarily useful" for intercepting electronic communications. The Wiretap Act (18 U.S.C. § 2511) makes it illegal to intentionally intercept electronic communications without permission.

Federal prosecutors typically combine the CFAA with §2512, the Wiretap Act, conspiracy, and wire fraud to build cases around a event, a practice known as charge stacking.

**Critique of the CFAA:**
- **The DOJ misrepresents writing as a crime:** The DOJ's press release announcing Hutchins's plea was titled "Marcus Hutchins Pleads Guilty to Creating and Distributing the Kronos Banking Trojan." Creating malware is not a crime although selling it to people you know are criminals is. The framing misrepresents the law.

- **Vague intent and authorization standards:** Core CFAA terms like "intent to cause damage," "exceeding authorized access," and "protected computer" have never been clearly defined by Congress or consistently interpreted by courts. Prosecutors decide what counts as criminal after the fact when beneficial for their case. Researchers cannot always predict whether their work will be charged.

- **Charge stacking creates plea pressure:** Federal prosecutors slice one crime into multiple counts under multiple statutes. Hutchins faced ten counts under the CFAA, the Wiretap Act, §2512, conspiracy, and wire fraud for what was essentially one criminal partnership with Vinny. Maximum exposure: 40 years. In these scenarios even defendants with viable defenses plead. Stacking is legal under the Blockburger test which says that the same conduct can be charged under multiple statutes as long as each requires proof of at least one element the others don't, yet it produces the punishment that double jeopardy was meant to prevent. This is why it's widely criticized for creating unjust outcomes in federal criminal law as a whole.

- **The law stays vague on purpose:** Pleas avoid trial. Without trials judges are never made to clarify or define what these terms actually mean. Each new researcher facing similar charges has no clearer answer than the last. The vagueness is not a flaw the system is working to fix...it is the leverage the system runs on.

**Critique of UK government complicity:**
- **GCHQ used him for WannaCry, then let him walk into the arrest:** Hutchins worked directly with the UK's National Cyber Security Centre which is part of GCHQ during the WannaCry response. He helped them keep the kill switch online and prevent a second wave. Three months later, GCHQ knew the FBI was investigating him for Kronos and planned to arrest him when he flew to DEFCON. Hutchins was not warned whatsoever. He boarded the flight and was arrested at the Las Vegas airport. The same agency that needed him during the attack stood by while another government grabbed him.

- **The UK had clear jurisdiction and didn't use it:** Hutchins lived in the UK and wrote the code in the UK. The Computer Misuse Act 1990 (the UK's main computer crime law) has covered "making, supplying, or obtaining articles for use in computer misuse offences" since 2006. UK prosecutors had clear authority to charge him but chose not to. Why?

- **The US could punish him harder:** US jurisdiction was based on a small amount of Kronos activity that touched US soil, which was enough under the CFAA's broad "protected computer" definition (any computer connected to the internet). Hutchins faced up to 40 years across his ten US counts under the CFAA. The same conduct under the UK's Computer Misuse Act carries a maximum of two to ten years per offense depending on the section but realistically sentences are much shorter. If anyone in either government wanted Hutchins to actually serve significant time then the US was the venue.

- **The UK did the US a quiet favor:** An anonymous UK government source told The Sunday Times the arrest "freed the British government and intelligence agencies from yet another headache of an extradition battle." The same source added: "Our US partners aren't impressed that some people who they believe to have cases against [them] for computer-related offences have managed to avoid extradition." The UK had repeatedly refused to extradite UK hackers like Gary McKinnon (blocked 2012) and Lauri Love (blocked 2018). Letting the US grab Hutchins on US soil evened the score without the UK government having to formally approve anything.

- **The UK avoided the political cost of prosecuting a national hero:** UK prosecution of Hutchins immediately after WannaCry would have politically been toxic. The press would have run the story of a young man who saved the NHS being charged by that same government for code he wrote as a teenager under blackmail. Public sympathy likely would have been on his side. Also likely, a UK trial produces a light sentence or acquittal. Letting the US prosecute meant the UK government could express "concern" while doing nothing and get the conviction without the political cost. Where someone is prosecuted is not always a legal question but a political one.

**Critique of who was charged vs. who wasn't:**
Out of every actor connected to either Kronos or WannaCry, only one was prosecuted: Hutchins. Everyone with more responsibility either couldn't be reached, was institutionally protected, or worked for the agency that built the exploit in the first place.

**Kronos:**

- **Hutchins:** Wrote the UPAS rootkit foundation around age 17. Refused to write the bank targeting web inject. Helped integrate code from a second programmer when blackmailed. Made approximately $8,000 from five sales of Kronos as of November 2014, according to FBI intercepted chats. Indicted on ten counts:

    1. Conspiracy to violate the CFAA and Wiretap Act
    2. Conspiracy to commit wire fraud
    3. Distributing a §2512 device (Kronos)
    4. Selling a §2512 device (Kronos)
    5. Promoting a §2512 device (Kronos)
    6. Advertising a §2512 device (Kronos)
    7. §2512 violations relating to UPAS Kit
    8. Unauthorized interception under the Wiretap Act
    9. Transmitting damaging code under the CFAA
    10. Lying to the FBI

    Pleaded guilty to two (counts 1 and 6). Eight were dropped. Time served.

- **Vinny:** Ran the operation. Marketed Kronos on AlphaBay and Russian forums. Hired and paid the second programmer to write the bank targeting web inject. Blackmailed Hutchins into continuing development by threatening to give his real name and address to the FBI. Took the bulk of the profits. The same indictment that charged Hutchins names Vinny as the unnamed co-conspirator on every count except count 10. Based on the descriptions in court documents, Vinny would face significantly more charges than Hutchins did:

    **Charges in the indictment (shared with Hutchins):**

    1. Conspiracy to violate the CFAA and Wiretap Act
    2. Conspiracy to commit wire fraud
    3. Distributing a §2512 device (Kronos)
    4. Selling a §2512 device (Kronos)
    5. Promoting a §2512 device (Kronos)
    6. Advertising a §2512 device (Kronos)
    7. §2512 violations relating to UPAS Kit
    8. Unauthorized interception under the Wiretap Act
    9. Transmitting damaging code under the CFAA

    **Additional charges Vinny alone would face based on his conduct:**

    10. Money laundering on Bitcoin proceeds (§1956)
    11. Wire fraud — multiple counts, each sale a separate count (§1343)
    12. Aggravated identity theft for use of stolen banking credentials (§1028A) — mandatory 2 year consecutive sentence per count
    13. Extortion via interstate communications for blackmailing Hutchins (§875(d))
    14. Separate conspiracy with the second programmer (§371)
    15. Separate conspiracies with each Kronos buyer who committed fraud (§371)
    16. Receiving stolen funds from buyers (§2315)
    17. Possibly RICO for running an ongoing criminal enterprise (§1962)

Federal prosecutors stacked ten counts against Hutchins under the same logic that produces the punishment double jeopardy was meant to prevent. Applying that same logic to Vinny, the operator they say ran the entire enterprise, produces seventeen+ counts and a conservative maximum exposure of around 160 years before any per sale wire fraud or per victim identity theft is fully broken out. Whether the government ever identified him is unknown. What is known is that he was never publicly named and he was never charged.

- **The unidentified second programmer:** Wrote the web inject which was the code that actually made Kronos a banking trojan. Without their work UPAS Kit was just a rootkit not a full bank targeting tool. Based on descriptions in court documents they would face the same §2512 and conspiracy charges Hutchins did in the same range or higher. The stacking math above gives us a sense of what the exposure looks like. Also never publicly identified. Also never charged.

- **The buyers:** People who paid up to $7,000 to use Kronos against actual bank customers. Some buyers were in the US, the UK, India, France, Germany, and Poland. Some were identified by researchers tracking the malware. Most were never charged.

**WannaCry:**

- **Hutchins:** Stopped the attack. Worked with the UK's National Cyber Security Centre on the response FOR FREE with no formal protection or recognition from the UK government. Three months later, he was the only individual federally prosecuted in connection with the WannaCry response on unrelated charges and the same UK government let him fly into FBI hands without warning.

- **NHS leadership:** Ignored a year of NHS Digital patch warnings. The National Audit Office confirmed the attack was preventable. Sir Chris Wormald, the Permanent Secretary at the Department of Health and Social Care, told the Public Accounts Committee in 2018 that "Cyber attacks and cyber crime are a fact of life. You are never completely safe from them, and indeed, if you believed you were completely safe from cyber crime, it would be an extremely bad sign." Nobody at NHS Digital, NHS England, or the Department of Health was fired, charged, fined, or formally disciplined. Instead(!) Sir Chris Wormald was promoted. Despite UK taxpayers paying an additional £196 million for cybersecurity through 2020 after WannaCry, a 2018 parliamentary audit found that all 200 NHS organizations checked still failed cybersecurity checks. The NHS continues to fail its legal obligation to protect patient data and has been breached every year since:

    - **2022:** LockBit took down NHS 111 emergency triage and stole 80,000 people's data
    - **2023:** Ransomware on Barts Health stole 70 terabytes of patient data
    - **2024:** NHS Scotland breached by Inc Ransom
    - **2024:** Alder Hey Children's Hospital and Wirral University Teaching Hospital both hit
    - **2024:** A ransomware attack on NHS contractor Synnovis disrupted more than 10,000 appointments at King's College Hospital and contributed to a patient's death
    - **2025:** Clop breached Barts Health a second time
    - **2025:** DevMan ransomware stole 300 GB from DXS International, the NHS GP software supplier serving 2000 GP practices
    - **2026:** NHS trusts hit by the 2024 Synnovis attack still operating without fully restored systems, with 161,560 pathology reports delayed at South London and Maudsley alone

- **The NSA:** Built EternalBlue, the exploit WannaCry depended on. Lost control of it when the Shadow Brokers leaked it in April 2017. No agency accountability and no public investigation.

- **Lazarus Group:** Conducted the actual attack. Out of US legal reach as a North Korean state actor.

**Why it matters for GRC:**
- **The law scares researchers off legitimate work:** Anyone writing security tools should worst case assume their code can be charged under the CFAA years later in a country they don't live in regardless of intent. Travel itself becomes a risk factor. Hutchins was arrested at an airport during a hacker conference, the standard professional event in the field.

- **Vague laws make compliance impossible:** The CFAA is so unclear that researchers cannot tell what is legal until a prosecutor decides. Since in many ways there is no clear rule to follow, that means "compliance" stops being a real thing. The only way to stay safe is to stay invisible: anonymous, off the record, and not traveling to the US. That punishes legitimate researchers who operate openly and rewards bad actors who already operate in the shadows. GRC teams advising on security research should document intent, scope, and authorization for every engagement. This documentation isn't a guarantee against prosecution, but it does make a case harder and gives the defense something concrete to point to.

- **Inevitability rhetoric is irresponsible:** When someone as high up as the Permanent Secretary at the UK Department of Health calls cyberattacks "a fact of life," they are making excuses in advance for future preventable vulnerabilities. Yes, breaches happen everywhere but this specific breach happened to the NHS because the NHS specifically ignored its specific patch warnings. "Breaches happen" is not a defense for "this breach has happened to us, again and again, for nearly a decade." Flag this kind of language in governance reviews.

- **Selective enforcement is built into the system:** The government catches people who are easy to find, not necessarily people who are most responsible. Vague laws, global jurisdiction, stacked charges, and plea deals work together to make this happen. This is what the system was built to do. GRC teams should understand that the visible target in any cyber incident is rarely the most culpable actor and act accordingly when communicating risk to leadership.

- **The pattern repeats until something changes:** Protecting patient data isn't a preference or a pet peeve I'm complaining about. It's a legal obligation. The NHS is breaking UK GDPR (incorporated into UK law via the Data Protection Act 2018) every single day it refuses to maintain adequate security measures to protect patient data. The same officials are still in charge. Patient services go offline. £196 million in taxpayer money has been spent. The NHS continues to operate above the laws every citizen is required to follow.

**Sources:**
- [hacker:HUNTER — WannaCry: The Marcus Hutchins Story (YouTube documentary)](https://www.youtube.com/watch?v=vveLaA-z3-o)
- [US Department of Justice — Marcus Hutchins Pleads Guilty to Creating and Distributing the Kronos Banking Trojan and UPAS Kit Malware](https://www.justice.gov/usao-edwi/pr/marcus-hutchins-pleads-guilty-creating-and-distributing-kronos-banking-trojan-and-upas)
- [US Department of Justice — Superseding Indictment Returned Against Marcus Hutchins](https://www.justice.gov/usao-edwi/pr/superseding-indictment-returned-against-marcus-hutchins)
- [US Department of Justice — Plea agreement for Marcus Hutchins (PDF)](https://www.justice.gov/usao-edwi/press-release/file/1153526/download)
- [Tripwire — MalwareTech, WannaCry and Kronos: Understanding the Connections](https://www.tripwire.com/state-of-security/malwaretech-wannacry-kronos-understanding-connections)
- [emptywheel (Marcy Wheeler) — An Inventory of MalwareTech's New Charges](https://emptywheel.net/2018/06/21/an-inventory-of-malwaretechs-new-charges/)
- [Krebs on Security — Marcus 'MalwareTech' Hutchins Pleads Guilty to Writing, Selling Banking Malware](https://krebsonsecurity.com/2019/04/marcus-malwaretech-hutchins-pleads-guilty-to-writing-selling-banking-malware/)
- [CyberScoop — Marcus Hutchins, who stopped WannaCry's spread, avoids prison time](https://cyberscoop.com/marcus-hutchins-sentenced-kronos-wannacry/)
- [Wired — The Confessions of Marcus Hutchins, the Hacker Who Saved the Internet](https://www.wired.com/story/confessions-marcus-hutchins-hacker-wannacry/)
- [Wikipedia — Marcus Hutchins](https://en.wikipedia.org/wiki/Marcus_Hutchins)
- [Wikipedia — Kronos (malware)](https://en.wikipedia.org/wiki/Kronos_(malware))
- [Malicious Life Podcast — Marcus Hutchins: A Controversial Hero](https://malicious.life/episode/episode-138/)
- [Group-IB — Kronos devouring its children](https://www.group-ib.com/blog/kronos/)
- [BleepingComputer — MalwareTech Arrested by the FBI on Charges of Creating Kronos Banking Trojan](https://www.bleepingcomputer.com/news/security/malwaretech-arrested-by-the-fbi-on-charges-of-creating-kronos-banking-trojan/)
- [EFF — Computer Fraud and Abuse Act Reform](https://www.eff.org/issues/cfaa)
- [Inside Privacy (Covington) — Is the Hutchins Indictment Over Malware Unconstitutional?](https://www.insideprivacy.com/united-states/litigation/is-the-hutchins-indictment-over-malware-unconstitutional/)
- [Inside Privacy (Covington) — Government's Response to Malware Defendant's Constitutional Challenge Falls Short](https://www.insideprivacy.com/data-security/governments-response-to-malware-defendants-constitutional-challenge-falls-short/)
- [Hansard / UK Parliament — Computer Misuse Act 1990](https://hansard.parliament.uk/commons/2022-04-19/debates/AE9413F3-D4F2-44EC-890E-75B0250328C4/ComputerMisuseAct1990)
- [Crown Prosecution Service — Computer Misuse Act guidance](https://www.cps.gov.uk/prosecution-guidance/computer-misuse-act)
- [The Register — British snoops at GCHQ knew FBI was going to arrest Marcus Hutchins](https://www.theregister.com/2017/08/21/gchq_knew_marcus_hutchins_risked_arrest_fbi/)
- [Computing — British authorities knew about US plans to arrest Marcus Hutchins](https://www.computing.co.uk/news/3015956/british-authorities-knew-about-us-plans-to-arrest-marcus-hutchins)
- [IBTimes UK — GCHQ knew WannaCry hero Marcus Hutchins would be 'walking into a trap'](https://www.ibtimes.co.uk/gchq-knew-wannacry-hero-marcus-hutchins-would-be-walking-into-trap-fbis-sting-1635846)
- [Computer Weekly — WannaCry hero Marcus Hutchins spared jail](https://www.computerweekly.com/news/252467486/WannaCry-hero-Marcus-Hutchins-spared-jail)
- [National Audit Office — Investigation: WannaCry cyber attack and the NHS](https://www.nao.org.uk/reports/investigation-wannacry-cyber-attack-and-the-nhs/)
- [House of Commons Public Accounts Committee — Cyber-attack on the NHS (PDF)](https://publications.parliament.uk/pa/cm201719/cmselect/cmpubacc/787/787.pdf)
- [Public Accounts Committee — Oral evidence: Investigation: WannaCry cyber attack and the NHS, 5 February 2018](https://committees.parliament.uk/oralevidence/10786/html/)
- [NHS England — Lessons learned review of the WannaCry Ransomware Cyber Attack (February 2018, PDF)](https://www.england.nhs.uk/wp-content/uploads/2018/02/lessons-learned-review-wannacry-ransomware-cyber-attack-cio-review.pdf)
- [Wikipedia — WannaCry ransomware attack](https://en.wikipedia.org/wiki/WannaCry_ransomware_attack)
- [Scientific American — WannaCry Report Shows NHS Chiefs Knew of Security Danger, but Management Took No Action](https://www.scientificamerican.com/article/wannacry-report-shows-nhs-chiefs-knew-of-security-danger-but-management-took-no-action/)
- [BleepingComputer — UK NHS suffers outage after cyberattack on managed service provider (Advanced, 2022)](https://www.bleepingcomputer.com/news/security/uk-nhs-suffers-outage-after-cyberattack-on-managed-service-provider/)
- [The Record — NHS software supplier Advanced faces £6m fine over ransomware attack failings](https://therecord.media/nhs-software-supplier-hit-with-6-million-fine)
- [BleepingComputer — UK fines software provider £3.07 million for 2022 ransomware breach](https://www.bleepingcomputer.com/news/security/uk-fines-software-provider-307-million-for-2022-ransomware-breach/)
- [TechCrunch — UK battles hacking wave as ransomware gang claims 'biggest ever' NHS breach (Barts Health, 2023)](https://techcrunch.com/2023/07/10/uk-hacks-public-sector-nhs-ransomware/)
- [TechCrunch — Ransomware hackers target NHS hospitals with new cyberattacks (Alder Hey, Wirral, 2024)](https://techcrunch.com/2024/12/04/ransomware-hackers-target-nhs-hospitals-with-new-cyberattacks/)
- [The Register — NHS confirms investigation into Clop cyberattack claim (November 2025)](https://www.theregister.com/2025/11/14/nhs_clop/)
- [TechCrunch — Tech provider for NHS England confirms data breach (DXS International, December 2025)](https://techcrunch.com/2025/12/18/tech-provider-for-nhs-england-confirms-data-breach/)
- [The Record — Ransomware attack continues to disrupt healthcare in London nearly two years later (January 2026)](https://therecord.media/ransomware-nhs-cyberattack-disruption)
- [The Record — Ransomware attack contributed to patient's death, says Britain's NHS](https://therecord.media/ransomware-attack-contributed-patient-death-uk-nhs)
- [HIPAA Journal — Patient Death Linked to Ransomware Attack on Pathology Services Provider](https://www.hipaajournal.com/patient-death-linked-to-ransomware-attack/)
- [Infosecurity Magazine — Patient Death Linked to NHS Cyber-Attack](https://www.infosecurity-magazine.com/news/patient-death-linked-nhs-cyber/)
- [Digital Health News — Patient death linked to cyber attack on NHS pathology provider](https://www.digitalhealth.net/2025/06/patient-dies-as-a-result-of-cyber-attack-on-nhs-pathology-provider/)
- [The Register — NHS supplier ends 18-month probe into cyberattack (Synnovis, November 2025)](https://www.theregister.com/2025/11/13/synnovis_qilin_investigation/)
- [NHS England — Synnovis cyber incident](https://www.england.nhs.uk/synnovis-cyber-incident/)
- [Cloudflare — What was the WannaCry ransomware attack?](https://www.cloudflare.com/learning/security/ransomware/wannacry-ransomware/)
- [Washington Post — How we know the NSA had access to internal Google and Yahoo cloud data](https://www.washingtonpost.com/world/national-security/how-we-know-the-nsa-had-access-to-internal-google-and-yahoo-cloud-data/2013/11/04/b4e4b2f2-456d-11e3-b6f8-3782ff6cb769_story.html)

---

## Executive Order 12333
*Added: April 19, 2026*

**Real-world example:**
In 2013, documents leaked by Edward Snowden revealed the MUSCULAR program. The NSA and its UK counterpart GCHQ tapped into the private underwater(!) fiber-optic links that connected Google's and Yahoo's data centers around the world. Before your email left Google's network to travel the public internet, it was encrypted. After it left, it was encrypted. But between Google's own data centers, on Google's own private cables, it was not encrypted because Google assumed that network was theirs. The NSA tapped those cables and collected hundreds of millions of records a day. Because the collection was happening outside of the US targeting non-US infrastructure, it required zero warrants, no FISA court approval, and no Section 702 certification. It was done legally under the authority of Executive Order 12333. An actual NSA slide describing the location of the tap had a smiley face drawn on it.

**What Executive Order 12333 is:**
This is an executive order (issued directly by the President without Congress voting on it) by President Reagan on December 4, 1981. It is the foundational authority governing how US intelligence conducts surveillance outside the US against non-US persons. It covers the CIA, NSA, DIA, and the intelligence arms of other agencies when they operate abroad. It came decades before FISA Section 702 (2008) and the Patriot Act (2001) but is still in effect today.

**Why "executive order" matters:**
Section 702, as flawed as it is, does at least have some oversight. Congressional committees, sunset clauses, FISA court review, public debate, etc. EO 12333 has almost none of that. It cannot be modified by Congress because it is an executive order. It has no sunset clause so it never expires and never provides a reauthorization conversation. It is not subject to FISA court review because the FISA court only covers FISA. The intelligence community interprets EO 12333 internally, with the rules for what to do when Americans' data gets swept up set by the agencies themselves. Most of what is done under it is classified. The public has almost no visibility into the largest category of US surveillance.

**Legislation from a different time:**
1981 was before the commercial internet, even before cellphones, before cloud computing, before undersea fiber-optic cables carried the majority of global communications, before Google existed, before email was common, before anyone imagined that a person in Illinois would have their private emails routed through servers in Ireland and back through London. EO 12333 was written for a world of embassies, foreign agents, and cold war intelligence yet is being applied to a world where the physical infrastructure of citizen communications happens to pass through foreign jurisdictions by default. The law has not caught up wiht the world that exists today. The permissions have not been adjusted...the surveillance has just expanded to fill the technology as it was built.

**Why it matters for GRC:**
Most corporate data flows through foreign infrastructure at some point. Overseas offices, international customers, cloud providers with centers/servers abroad, and routine traffic that crosses borders invisibly. All of this is potentially exposed to EO 12333 collection and that exposure cannot be contracted around by any "privacy focused" company or service. For GRC teams negotiating with EU customers, EO 12333 is part of why Schrems II was decided the way it was: US surveillance law including the parts that the US government would prefer not to discuss gives intelligence agencies access that violates GDPR standards. Understanding EO 12333 matters for honest risk assessments. You cannot tell a customer their data is protected from US government access if it passes through infrastructure the US government can legally tap at any time for any amount of time without a warrant.

**Sources:**
- [Washington Post - How we know the NSA had access to internal Google and Yahoo cloud data](https://www.washingtonpost.com/world/national-security/how-we-know-the-nsa-had-access-to-internal-google-and-yahoo-cloud-data/2013/11/04/b4e4b2f2-456d-11e3-b6f8-3782ff6cb769_story.html)
- [EFF - EO 12333: End Mass Surveillance Under Executive Order 12333](https://www.eff.org/deeplinks/2014/01/eo-12333-end-mass-surveillance-under-executive-order-12333)
- [ACLU - Executive Order 12333: Unchecked Surveillance of Americans](https://www.aclu.org/report/executive-order-12333-unchecked-surveillance-americans)
- [ODNI - Executive Order 12333 (official text)](https://www.dni.gov/index.php/ic-legal-reference-book/executive-order-12333)
- [Brennan Center - What the Government Does with Americans' Data](https://www.brennancenter.org/our-work/research-reports/what-government-does-americans-data)

---

## The Wyden Letter
*Added: April 19, 2026*

**Real-world example:**
On March 26, 2026 six Democratic lawmakers: Senators Ron Wyden, Alex Padilla, Ed Markey, and Elizabeth Warren, plus Rep. Sara Jacobs and Rep. Pramila Jayapal sent a formal letter to Director of National Intelligence Tulsi Gabbard. The letter asks her to publicly clarify whether Americans who use commercial VPN services are being treated as foreigners for surveillance purposes and so losing their protections under the Fourth Amendment. As of now, Gabbard has not responded. The timing was intentional as the letter was sent while Congress is actively debating Section 702 reauthorization which forces the VPN question into the fight.

**The core question:**
VPNs route internet traffic through servers in other locations to hide a user's real location. That is the point. But under Section 702 the government can obtain foreign communications without a warrant. If an American's traffic exits through a VPN server in Amsterdam, does the intelligence community treat that traffic as Dutch/foreign/okay to collect without a warrant? The lawmakers are asking Gabbard to say publicly whether this is happening or not. If yes, it means a privacy tool is actually stripping Americans of their Fourth Amendment rights. If no, Gabbard should say so on the record. Her refusal to answer is an answer in itself.

**Why it matters for GRC:**
The letter exposes the gap between what privacy tools are marketed/aim to do and how they are manipulated and misused under the law. GRC teams advising on data handling need to understand that where infrastructure is physically located matters for compliance, not just for marketing. A VPN being "privacy-focused" does not automatically mean stronger legal protection for users and in some cases may mean the opposite. For organizations with employees or clients using commercial VPNs, the categorization question affects what laws actually apply to their communications. The letter is also a good example of how Congress actually forces answers from the executive branch: put the question in writing, make it public, time it to a vote.

**Sources:**
- [Nextgov - Lawmakers question VPN impact on Americans' FISA surveillance protections](https://www.nextgov.com/cybersecurity/2026/03/lawmakers-question-vpn-impact-americans-fisa-surveillance-protections/412437/)
- [Android Authority - Do US-based VPN users risk being treated as foreign surveillance targets?](https://www.androidauthority.com/using-vpn-could-allow-us-government-surveillance-3652311/)
- [The Meridiem - VPN Privacy Inflection as Overseas Routing May Trigger NSA Surveillance](https://themeridiem.com/tech-policy-regulation/2026/03/26/vpn-privacy-inflection-as-overseas-routing-may-trigger-nsa-surveillance)

---

## Section 702 FISA
*Added: April 19, 2026*

**Real-world example:**
Section 702 was supposed to expire April 20, 2026 unless Congress reauthorizes it. As of tonight, the fight is live. The Trump administration pushed for a clean 18-month reauthorization with no changes. House blocked amendments that would have required warrants for searching Americans' data. On April 17, two back-to-back votes failed. Those were 1: a five-year package with modest reforms which collapsed when roughly a dozen Republicans rejected it and 2: the procedural vote for the clean 18 month extension failed 197-228, with 20 Republicans defying Trump and 4 Dems also voting no. Around 2am the House passed a 10 day stopgap, pushing the deadline to April 30. DNI Tulsi Gabbard, who previously opposed 702 as a congresswoman and co-sponsored legislation to repeal it, reversed position again saying warrants should be required for US person queries which goes against Trump. The reform coalition cuts across both parties (Freedom Caucus Republicans plus progressive Democrats). The coalition protecting 702 also spans across both parties. Outcome unclear.

**What is Section 702:**
A surveillance authority passed in 2008 as part of the FISA Amendments Act. It allows the US government to collect emails, phone calls, and text messages of non-US persons located outside of the US without a warrant. Targets are selected by intelligence analysts, not courts. The Attorney General and DNI issue annual "certifications" (very broad/bulk request like "We want to spy on foreign cyber threats") that the FISA court reviews and generally approves. The FISA court does not approve individual targets. Any American who communicates with a foreign target can have their communications swept into the 702 database as "incidental collection."

**The loophole:**
Once Americans' communications are in the 702 database, the FBI can search them for US person information without a warrant. These are called "US person queries" or backdoor searches. The FISA Court found in 2022 that "compliance problems with the FBI's querying of Section 702 information have proven to be persistent and widespread." From 2020 to 2021 alone, the FBI conducted 278,000 noncompliant searches that the DOJ determined violated FBI standards. Documented abuses include searches targeting Black Lives Matter protesters, January 6 participants, a congressional campaign's 19,000 donors, a US Senator, a state senator, and a state judge. A 2024 federal court ruling held that these backdoor searches are unconstitutional and ordinarily require a warrant. Congress has reauthorized 702 multiple times despite the abuses.

**Why it matters for GRC:**
Section 702 is why US cloud services struggle with EU data protection compliance. The EU's Schrems II ruling in 2020 found that US surveillance law, specifically 702, gives US intelligence agencies too much access to European data which violates GDPR. Any organization handling EU citizen data through US based infrastructure is exposed to this. GRC teams at multinational companies spend significant time managing this tension. For US companies specifically, 702 shapes what, if any privacy assurances can legally be made to customers, because no contractual clause overrides surveillance authority like 702. The live reauthorization fight also illustrates how surveillance law actually changes in practice: not through clean reform but through coalition fights, sunset clauses, and last minute procedural maneuvers.

**Sources:**
- [The Hill - GOP rebels block FISA Section 702 spy powers deal](https://thehill.com/homenews/house/5835879-fisa-702-spy-powers-vote/)
- [NPR - Congress extends controversial surveillance powers for 10 days](https://www.npr.org/2026/04/17/nx-s1-5788573/house-extends-surveillance-powers-for-10-days)
- [Brennan Center - Section 702 of the Foreign Intelligence Surveillance Act](https://www.brennancenter.org/our-work/research-reports/section-702-foreign-intelligence-surveillance-act)
- [Wikipedia - FBI Section 702 query violations](https://en.wikipedia.org/wiki/FBI_Section_702_query_violations)
- [EFF - Federal Court Rules Backdoor Searches of 702 Data Unconstitutional](https://www.eff.org/deeplinks/2025/01/victory-federal-court-finally-rules-backdoor-searches-702-data-unconstitutional)
- [ABC News - Tulsi Gabbard shifts stance on key surveillance tool](https://abcnews.go.com/Politics/tulsi-gabbard-shifts-stance-key-surveillance-tool-previously/story?id=117587144)

---

## Swiss Surveillance Law (VÜPF)
*Added: March 5 2026*

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

**Sources:**
- [TechRadar - Is Proton leaving Switzerland?](https://www.techradar.com/vpn/vpn-privacy-security/is-proton-leaving-switzerland-legal-uncertainty-of-proposed-surveillance-laws-is-pushing-them-to-make-several-changes)
- [Heise - Surveillance: Proton relocates parts of its infrastructure from Switzerland](https://www.heise.de/en/news/Surveillance-Proton-relocates-parts-of-its-infrastructure-from-Switzerland-10538664.html)
- [Tuta - Switzerland plans surveillance worse than US](https://tuta.com/blog/switzerland-surveillance-plan)
- [DoVPN - Switzerland's new VPN surveillance plan](https://dovpn.com/swiss-vpn-surveillance-protonvpn-privadovpn/)

---

## Encryption vs. Metadata
*Added: March 5 2026*

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

**Sources:**
- [TechCrunch - ProtonMail logged IP address of French activist after order by Swiss authorities](https://techcrunch.com/2021/09/06/protonmail-logged-ip-address-of-french-activist-after-order-by-swiss-authorities/)
- [The Register - ProtonMail deletes 'we don't log your IP' boast from website](https://www.theregister.com/2021/09/07/protonmail_hands_user_ip_address_police/)
- [CyberInsider - Proton Mail payment data helped FBI identify 'Stop Cop City' account holder](https://cyberinsider.com/proton-mail-payment-data-helped-fbi-identify-stop-cop-city-account-holder/)
- [Proton - Transparency Report](https://proton.me/legal/transparency)

---

## Mutual Legal Assistance Treaties (MLATs)
*Added: March 5 2026*

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
- Only available to government officials, usually prosecuters - not private citizens or civil cases
- Requests must go through formal legal processes and be approved by a court in receiving country
- The US has MLATs with 65+ countries including Switzerland, the UK, and all EU member states for starters

**Why it matters for GRC:**
Organizations operating internationally need to understand that legal obligations cross borders. Privacy tools protect content, but metadata and account information can still be captured legally. Compliance teams should consider how MLATs affect who can legally access data and where.

**Sources:**
- [TechCrunch - ProtonMail logged IP address of French activist after order by Swiss authorities](https://techcrunch.com/2021/09/06/protonmail-logged-ip-address-of-french-activist-after-order-by-swiss-authorities/)
- [Proton - Important clarifications regarding arrest of climate activist](https://proton.me/blog/climate-activist-arrest)
- [Proton - Transparency Report](https://proton.me/legal/transparency)








