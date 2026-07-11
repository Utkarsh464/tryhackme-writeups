# Cache Me Outside — Tasks

## Task 1: Challenge Questions

### Question 1 — What is the retired hacker's full name?

**Approach:**
The room provides a conversation screenshot which contains a Komoot profile URL:
`https://www.komoot.com/user/5667624959835`

Opening this profile reveals the user's full name directly on their public Komoot page. The bio describes them as an ex-hacker turned runner, starting a security consulting firm.

**Answer:** `Jim Lee`

---

### Question 2 — What email address did he accidentally expose?

**Approach:**
The Komoot profile bio links to a GitHub account: `github.com/jiml33t`

The GitHub profile has one pinned repository (`jiml33t/jiml33t`) with a single commit. Git commit metadata stores the author's email address. Using the GitHub API or appending `.patch` to the commit URL reveals the raw commit data:

```
https://api.github.com/repos/jiml33t/jiml33t/commits
```

Or directly viewing the patch:
```
https://github.com/jiml33t/jiml33t/commit/7b2c8e0a540c36f2e09da5945066020621d6a059.patch
```

The author field contains:
```
author jimleepro1-cell <jimleepro1@gmail.com>
```

**Answer:** `jimleepro1@gmail.com`

---

### Question 3 — What is his phone number?

**Approach (Active OSINT):**
This step involves sending an email to `jimleepro1@gmail.com`. An automated out-of-office reply is configured on the account, which includes his phone number in the email signature:

The auto-reply contains:
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

**Warning:** In real-world investigations, interacting with discovered infrastructure can alert the target and should only be done with proper authorization.

**Answer:** `+40 743 321 239`

---

### Question 4 — In which city is he located?

**Approach:**
Searching for the username `jiml33t` across social media platforms reveals a Threads profile: `threads.com/@jiml33t`

A post dated 05/07/26 reads:
> "Just finished my last run before the big day, hopping on the tram for my well-deserved coffee at my favourite French supermarket."

The attached photo contains a visible sign reading **"IRIGATII.RO"**. The `.ro` top-level domain indicates Romania. Running the image through Google Lens confirms the location is along **Calea Buziașului** in **Timișoara, Romania**.

**Answer:** `Timișoara`

---

### Question 5 — Submit the name of the tram station where he got off on the 7th of May, 2026.

**Approach:**
Using the geolocated position on Calea Buziașului in Timișoara, the nearest tram station in the direction matching the Threads post is identified. The post mentions going to a "French supermarket" — the nearest supermarket to that tram stop is consistent with the route.

The closest tram stop is:

**Answer:** `Piața Gheorghe Domășneanu`

---

## Summary

| Question | Answer |
|----------|--------|
| Full name | Jim Lee |
| Exposed email | jimleepro1@gmail.com |
| Phone number | +40 743 321 239 |
| City | Timișoara |
| Tram station | Piața Gheorghe Domășneanu |

## Key Takeaways

1. **Public profiles leak more than you think** — Komoot, Strava, and other fitness apps often display real names publicly
2. **Git history is permanent** — commit metadata (author name, email) persists forever and is easily accessible via API or `.patch` files
3. **Auto-replies are a goldmine** — out-of-office email responses frequently include phone numbers and other sensitive details
4. **Social media images contain hidden data** — a single sign or storefront in a photo can geolocate a person to a specific city or street
5. **Username reuse enables cross-platform correlation** — the same `jiml33t` handle appeared on Komoot, GitHub, Threads, and Instagram
