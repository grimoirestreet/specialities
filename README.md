# 🜂 Grimoire Street • Specialties Tracker

This tracker powers the **Specialties Availability Table** and **Roster** on your site.
It automatically loads data from the `tracker.json` file in this repository and updates whenever you commit changes.

No coding knowledge is required — you only edit a single JSON file.

---

## 📂 Files in This Repo

```
specialities/
 ├─ tracker.json         ← Main data file (edit this for roster changes)
 ├─ index.html           ← Tracker webpage (reads tracker.json automatically)
 └─ README.md            ← This guide
```

---

## 📝 Adding a New Character

1. **Open** `tracker.json` in GitHub.

2. Click the **pencil icon** in the top-right corner to edit the file.

3. Scroll to the bottom (before the closing `]`).

4. Copy the template below and paste it on a **new line**:

   ```json
   {
     "specialty": "Parselmouth",
     "character": "Full Name Here",
     "house": "Gryffindor",
     "year": "1",
     "player": "@DiscordName#0000",
     "status": "Approved",
     "app": "https://link.to/application",
     "notes": "Optional notes here"
   }
   ```

5. **Update the fields** with the correct info:

| Field     | Type   | Allowed Values                                                                                                | Notes                      |
| --------- | ------ | ------------------------------------------------------------------------------------------------------------- | -------------------------- |
| specialty | string | Parselmouth, Occlumens, Legilimens, Seer, Metamorphmagus, Blood Curse Bearer, Obscurial, Wandless Magic Adept | Must match exactly         |
| character | string | Any full name                                                                                                 | Character’s full name      |
| house     | string | Gryffindor, Hufflepuff, Ravenclaw, Slytherin, `— Staff / Adult —`, `—`                                        | Use `—` for NPCs or adults |
| year      | string | "1"–"7" for students, "—" for adults                                                                          |                            |
| player    | string | Discord handle like `@Name#1234`                                                                              |                            |
| status    | string | Approved, Pending, On Hiatus, Retired, Deceased                                                               |                            |
| app       | string | URL link to application or profile                                                                            |                            |
| notes     | string | Any extra details (optional)                                                                                  | Optional free text         |

6. **Add a comma** `,` **after the block** unless it’s the last entry.
7. Scroll down and click **Commit changes** to save.

---

## 🧑‍🏫 Marking a Character as an Adult

A character is treated as an **adult** (not counted toward student caps) if **both**:

* Their `house` is set to `— Staff / Adult —`
* Their `year` is set to `—`

Example:

```json
{
  "specialty": "Occlumens",
  "character": "Professor Selene Graves",
  "house": "— Staff / Adult —",
  "year": "—",
  "player": "@ProfessorGraves",
  "status": "Approved",
  "app": "https://link.to/application",
  "notes": "Teaches Defense Against the Dark Arts"
}
```

This keeps the **Current Availability** table correct:

* **Students**: Year `1–7` and any Hogwarts house name
* **Adults**: Year `—` and `house` = `— Staff / Adult —`

---

## ✏️ Editing a Character

* Find the character’s `{ ... }` block in `tracker.json`.
* Change any values you need (name, status, year, etc.).
* Click **Commit changes**.

---

## ❌ Removing a Character

* Delete the character’s `{ ... }` block.
* Make sure commas stay correct:

  * All entries except the **last one** need a comma after the `}`.
  * The last entry in the file must **not** have a trailing comma.

---

## 📄 JSON Template (Copy & Paste)

```json
[
  {
    "specialty": "Parselmouth",
    "character": "Full Name Here",
    "house": "Gryffindor",
    "year": "1",
    "player": "@DiscordName#0000",
    "status": "Approved",
    "app": "https://link.to/application",
    "notes": "Optional notes here"
  }
]
```

Copy the **entire block inside the \[ ] array** and paste it on a new line before the `]` when adding multiple characters.

---

## ✅ Example with Two Characters

```json
[
  {
    "specialty": "Parselmouth",
    "character": "Ivy Blackthorne",
    "house": "Slytherin",
    "year": "5",
    "player": "@PlayerOne",
    "status": "Approved",
    "app": "https://link.to/app1",
    "notes": "Known for keeping snakes in the dorms"
  },
  {
    "specialty": "Seer",
    "character": "Alaric Moon",
    "house": "Ravenclaw",
    "year": "6",
    "player": "@PlayerTwo",
    "status": "Pending",
    "app": "https://link.to/app2",
    "notes": "Has visions during thunderstorms"
  }
]
```

---

## ⚠️ Common Mistakes to Avoid

* **Missing commas** → Every entry except the last one needs a comma after the closing brace `}`.
* **Wrong quotes** → All text values must use `"double quotes"`.
* **Mismatched specialties** → Must match exactly: e.g., `Parselmouth`, not `parselmouth`.
* **Year values** → Use `"—"` for adults, `"1"`–`"7"` for students.

---

## 🔄 Live Updates

* Once you commit changes, the tracker webpage automatically shows the new data after a refresh.
* No need to edit `index.html` or JavaScript.
