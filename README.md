# 🔐 Lab 11 - Phishing Analysis Fundamentals

---

## Lab Environment

| Item | Details |
|---|---|
| Platform | TryHackMe |
| Room | Phishing Analysis Fundamentals |
| Email Client | Mozilla Thunderbird |
| Text Editor | Mousepad |
| Decoder | CyberChef, ipvoid |
| Email Samples | `email1.eml`, `email2.txt`, `email3.eml` |

<img width="630" height="495" alt="image" src="https://github.com/user-attachments/assets/1f97b66e-7527-4a25-a788-97f5c0871de9" />

---

## email1.eml — Header Analysis

Opened `email1.eml` in Thunderbird.

<img width="421" height="333" alt="image" src="https://github.com/user-attachments/assets/ac93c1eb-716c-41c9-9c2b-91332333c611" />

Viewed raw message source using `Ctrl + U` to extract header fields.

<img width="1264" height="455" alt="image" src="https://github.com/user-attachments/assets/4cea63e1-8664-4892-ba74-0563c0a33348" />

| Field | Value |
|---|---|
| Subject | `Help protect your budget by protecting your home` |
| X-Originating-IP | `43.255.56.161` |

<img width="645" height="434" alt="image" src="https://github.com/user-attachments/assets/aa9b2976-07af-44fe-8fc4-5db91f1fc219" />

---

## email2.txt — Attachment Extraction

Opened `email2.txt` in Mousepad to inspect the raw attachment data.

<img width="626" height="342" alt="image" src="https://github.com/user-attachments/assets/d94aff40-9eb1-4039-a559-06e51f347138" />

Identified the attachment headers:

| Field | Value |
|---|---|
| Content-Type | `application/pdf` |
| Filename | `zmqpalgh.pdf` |
| Encoding | `base64` |

<img width="504" height="187" alt="image" src="https://github.com/user-attachments/assets/a78be363-4eca-44c9-919e-c1b9b1ac8b90" />

Copied the Base64 content from the raw source.

<img width="436" height="327" alt="image" src="https://github.com/user-attachments/assets/61bfb5e7-157e-46a2-ae2e-2f6a7ca9dda5" />

Pasted into [ipvoid Base64 to PDF](https://www.ipvoid.com/base64-to-pdf/) to reconstruct the PDF.

<img width="421" height="50" alt="image" src="https://github.com/user-attachments/assets/32f62f04-7af3-4983-82f5-d11db3eab239" />

<img width="493" height="482" alt="image" src="https://github.com/user-attachments/assets/702a3ae2-e266-4fc1-971d-0b0ef861d20c" />

The reconstructed PDF revealed the hidden flag:

<img width="292" height="124" alt="image" src="https://github.com/user-attachments/assets/4f77945c-ab15-4d36-b49d-6cbd340a9268" />

```
THM{BENIGN_PDF_ATTACHMENT}
```

---

## email3.eml — Phishing Indicators

Opened `email3.eml` in Thunderbird and viewed the message source.

<img width="1248" height="314" alt="image" src="https://github.com/user-attachments/assets/ff8fab2f-ef8b-435e-a55e-6bbed3cf496e" />

| Indicator | Value |
|---|---|
| Spoofed Organization | `Home Depot` |
| Sender Email | `support@teckbe.com` |
| X-Originating-IP | `103.234.236.83` |
| Defanged IP | `103[.]234[.]236[.]83` |
| Authentication-Results Server | `atlas102.free.mail.gq1.yahoo.com` |

The sender display name showed `Thank you! Home Depot` but the actual domain was `teckbe.com`, a clear brand impersonation attempt.

Defanged the IP using CyberChef.

<img width="459" height="339" alt="image" src="https://github.com/user-attachments/assets/16112110-831a-4f43-ac55-1afbad727df0" />

<img width="230" height="310" alt="image" src="https://github.com/user-attachments/assets/19863c02-2a64-42fa-87ab-8ad6d8dbdaf3" />

<img width="409" height="85" alt="image" src="https://github.com/user-attachments/assets/3ae30baf-0488-436f-8eee-6478b93917b1" />

---

## Room Completed

<img width="983" height="558" alt="image" src="https://github.com/user-attachments/assets/4c9fc7f0-fef5-40ea-88f7-668bfb3ba046" />
