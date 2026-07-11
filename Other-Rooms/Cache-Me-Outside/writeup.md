# Cache Me Outside — Full OSINT Walkthrough

## Room Overview

**Cache Me Outside** is a medium-difficulty OSINT room on TryHackMe that simulates a real-world investigation. You are given a single screenshot of a conversation and must trace the digital footprint of a retired hacker who has left clues across multiple public platforms.

The five questions require you to:
1. Identify the person's full name
2. Find an accidentally exposed email address
3. Discover their phone number
4. Geolocate their city
5. Pinpoint a specific tram station

---

## Step 1: Starting Point — The Komoot Profile

The conversation screenshot contains a Komoot URL:
```
https://www.komoot.com/user/5667624959835
```

Komoot is an outdoor activity platform where users log runs, hikes, and cycling routes. Public profiles display the user's real name, bio, and sometimes linked accounts.

Opening the profile reveals:

| Field | Value |
|-------|-------|
| Name | **Jim Lee** |
| Bio | "Ex-hacker turning life around, running, starting own company" |
| Linked Account | `github.com/jiml33t` |

**Key OSINT principle:** Fitness and outdoor apps are often overlooked as OSINT sources, but users frequently use their real names on them, unlike more security-conscious platforms.

---

## Step 2: GitHub — The Email Leak

The GitHub profile `github.com/jiml33t` has one pinned repository: `jiml33t/jiml33t` (the profile README repo). It has a single commit.

Git stores author metadata (name and email) with every commit. This data is publicly accessible through:

**Method A — GitHub API:**
```
GET https://api.github.com/repos/jiml33t/jiml33t/commits
```

**Method B — .patch file:**
Append `.patch` to the commit URL:
```
https://github.com/jiml33t/jiml33t/commit/7b2c8e0a540c36f2e09da5945066020621d6a059.patch
```

The commit metadata reveals:
```
author jimleepro1-cell <jimleepro1@gmail.com>
```

**Why this works:** Git commits are immutable — even if you delete and recreate a repo, any forks or cached copies preserve the original commit data. The `.patch` view shows the exact diff along with author/committer metadata.

---

## Step 3: Email Auto-Reply — Phone Number Discovery (Active OSINT)

Sending an email to `jimleepro1@gmail.com` triggers an automated out-of-office reply:

```
Good day,
I will be absent from the office while I prepare for a marathon.
You can contact me on my phone for anything urgent.

Best Regards,
JL

JIM LEE
CYBERSECURITY CONSULTANT
jimleepro1@gmail.com
L33T SECURITY
+40 743 321 239
```

The phone number `+40 743 321 239` is a Romanian mobile number (+40 country code).

**Active OSINT note:** This step involves directly interacting with the target's infrastructure. In real investigations, this requires proper authorization and caution. The room explicitly includes this as a controlled exercise.

---

## Step 4: Threads — Geolocation via Image OSINT

Searching the username `jiml33t` across platforms leads to a Threads profile:
```
https://www.threads.com/@jiml33t
```

A post dated **May 7, 2026** reads:
> "Just finished my last run before the big day, hopping on the tram for my well-deserved coffee at my favourite French supermarket."

The attached photo contains a billboard with the text **IRIGATII.RO**.

### Image Geolocation Process

1. The `.ro` domain confirms Romania
2. Google Lens reverse image search on the photo identifies the exact location
3. The sign "IRIGATII.RO" is a company located on **Calea Buziașului, Timișoara**
4. This establishes Jim Lee's city as **Timișoara**

---

## Step 5: Tram Station Identification

Given:
- **Date:** May 7, 2026
- **Mode:** Tram
- **Destination:** French supermarket (likely Auchan or similar)
- **Starting location:** Calea Buziașului area

Working backward from the photo's location on Calea Buziașului, the nearest tram stop in the direction described is **Piața Gheorghe Domășneanu** (also known as Liviu Rebreanu - AEM).

This matches the tram route that would take someone from that area toward the identified supermarket.

---

## Complete Answer Summary

| # | Question | Answer | Source |
|---|----------|--------|--------|
| 1 | Full name | **Jim Lee** | Komoot public profile |
| 2 | Exposed email | **jimleepro1@gmail.com** | GitHub commit `.patch` metadata |
| 3 | Phone number | **+40 743 321 239** | Email auto-reply signature |
| 4 | City | **Timișoara** | Threads photo geolocation (IRIGATII.RO sign) |
| 5 | Tram station | **Piața Gheorghe Domășneanu** | Transit route from Calea Buziașului |

---

## OSINT Lessons Learned

1. **Username reuse is your biggest enemy** — `jiml33t` was used on Komoot, GitHub, Threads, and Instagram, making cross-platform correlation trivial
2. **Git commits are forever** — even a single commit with a README exposes author metadata
3. **Auto-replies don't think** — automated email responses often include phone numbers, addresses, and other PII
4. **Photos leak location data** — not just EXIF metadata, but visible signs, storefronts, and landmarks in images
5. **Transit routes can be reverse-engineered** — a post mentioning a tram + a geolocated photo + knowledge of local supermarkets = specific stop identification
6. **Passive OSINT first, active OSINT last** — always exhaust public information before interacting with targets

---

## Alternative Tools & Techniques

- **Sherlock/Holehe/Maigret**: Enumerate `jiml33t` across hundreds of platforms
- **ExifTool**: Extract metadata from images (though Threads/Instagram strip EXIF)
- **Google Maps Street View**: Confirm tram stops and supermarket locations visually
- **Whois**: Domain registration lookup for `irigatii.ro` (not needed here but useful in other investigations)
