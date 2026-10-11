# Task 3 — SQL Injection on DVWA (Low Security): Findings

**Intern:** Neo Masobela  |  **Track:** Cyber Security  |  **Internship:** Oasis Infobyte (OIBSIP)
**Environment:** DVWA (Damn Vulnerable Web Application) running locally at `http://127.0.0.1/dvwa`, security level **Low**
**Scope:** A deliberately vulnerable training application in a controlled local lab. No real website was tested.

---

## 1. Summary

A classic SQL injection was demonstrated in DVWA's SQL Injection module. A **normal** User ID (`1`) returned **one** record. The payload `1' OR '1'='1` made the same page return **five** records.

**Main result:** the application accepted text that changed the meaning of its database query. This is the core idea of SQL injection.

---

## 2. Test Setup

| Item | Details |
|---|---|
| Application | DVWA, SQL Injection module |
| Address | `http://127.0.0.1/dvwa/vulnerabilities/sqli/` |
| Security level | Changed from **Impossible** to **Low** on the DVWA Security page, and confirmed as "currently: low" |
| Method | Input typed into the **User ID** box and sent with the Submit button (the value appears in the page address as `id=...`) |
| Preparation | The DVWA database was set up before the test (shown at the start of the recording) |

---

## 3. Key Findings

| # | Finding | Evidence in the recording |
|---|---|---|
| F1 | A normal input returned **one** record | User ID `1` → `ID: 1`, `First name: admin`, `Surname: admin` |
| F2 | The injected input returned **five** records | Payload `1' OR '1'='1` → five results (see table below) |
| F3 | The input was **not checked or cleaned**, so it changed the query's logic | The same input box accepted a quote character and extra SQL-style text and gave a different result |
| F4 | The payload is visible in the page address | The address after the injection contains `id=1'+OR+'1'%3D'1&Submit=Submit` |

### Results returned by the payload

| # | First name | Surname |
|---|---|---|
| 1 | admin | admin |
| 2 | Gordon | Brown |
| 3 | Hack | Me |
| 4 | Pablo | Picasso |
| 5 | Bob | Smith |

### Normal vs injected

| | Normal input | Injected input |
|---|---|---|
| Input | `1` | `1' OR '1'='1` |
| Records returned | **1** | **5** |

---

## 4. Why It Happened (in simple terms)

1. The page asks the database: "give me the user whose ID is *what the visitor typed*".
2. With `1`, the question is clear, and only one user matches.
3. With `1' OR '1'='1`, the quote mark ends the typed value early, and `OR '1'='1'` adds a condition that is **always true**.
4. Because the condition is true for every row, the database returns **every user**, not just one.

*Note: the source code behind the page was not shown in the recording. This explanation is based on how the page behaved.*

---

## 5. Impact (if this were a real application)

- Unauthorized people could read data they should not see. The size of the problem depends on the application's query and the database account's permissions.
- In this demo only first and last names were displayed.
- Other kinds of injection (for example, reading other tables) were **not** tested here.

**Risk rating:** High if found in a real application, because it can expose stored data. In this lab it is expected, since DVWA is built to be vulnerable.

---

## 6. Recommendations

1. **Use parameterized queries (prepared statements).** The user's input is then treated as data and never as SQL code. This is the main fix.
2. **Validate input.** Accept only the expected format (for example, numbers for an ID).
3. **Use a low-privilege database account**, so a mistake can reach less data.
4. **Hide detailed database errors** from users.
5. **Add layers of defense**, such as a web application firewall, and test regularly.

DVWA's own Security page describes the **Impossible** level as the secure version, meant for comparing against the vulnerable code.

---

## 7. Limitations

- Only the **Low** security level was tested. Medium, High and Impossible were not tried.
- Only one payload was used (`1' OR '1'='1`).
- The results come from a training application and do not describe any real system.

---

## 8. Conclusion

At the Low security level, DVWA's SQL Injection page returned one record for a normal ID and five records when the always-true payload `1' OR '1'='1` was entered. This shows how unsafe handling of user input can let an attacker change a database query. The key defence is to use **parameterized queries (prepared statements)** so input is always treated as data.

---

## 9. Evidence

- Demonstration video: `Neo_Masobela_Task3_SQL_Injection_DVWA.mp4` (1:55, with voiceover)
- Voiceover script: `Task3_Voiceover_Script.md`
- Screenshots (to add): normal result for User ID `1`, the typed payload, and the five-record result

---

**Disclaimer:** All activity was performed on a deliberately vulnerable application in a controlled local virtual machine environment for educational and cybersecurity training purposes. No external or unauthorized systems were targeted.
