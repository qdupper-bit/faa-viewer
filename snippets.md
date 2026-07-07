# ThriveCart embed snippets

Replace `YOUR-USERNAME` once, then copy-paste per lesson. Each snippet goes in a **Custom HTML** element.

---

## Carburetors — the test page

PHAK Chapter 7 (FAA-H-8083-25C). Printed page 7-8 is where **Carburetor Systems** begins (float-type carburetor diagram); **Carburetor Icing** is 7-9 and **Carburetor Heat** is 7-10. Physical pages in `phak-ch07.pdf`: 8, 9, 10.

```html
<iframe
  src="https://YOUR-USERNAME.github.io/faa-viewer/index.html?file=pdfs/phak-ch07.pdf&page=8&title=PHAK%20Ch.7%20-%20Carburetor%20Systems"
  width="100%" height="720" style="border:0;border-radius:8px;"
  loading="lazy" title="FAA Reference - Carburetor Systems"></iframe>
```

Note: the Airplane Flying Handbook itself has no carburetor *systems* section — it only references carb heat procedurally (e.g., "carburetor heat off" during go-arounds, AFH Ch.9). The PHAK is the FAA's systems text, which is why this snippet points there.

---

## Template for any lesson

```html
<iframe
  src="https://YOUR-USERNAME.github.io/faa-viewer/index.html?file=pdfs/FILE.pdf&page=N&title=TITLE%20HERE"
  width="100%" height="720" style="border:0;border-radius:8px;"
  loading="lazy" title="FAA Reference"></iframe>
```

- `file=` — the filename you uploaded to `pdfs/` (case-sensitive)
- `page=` — physical page of that chapter file (printed X-N = page N, unless the edition adds a cover sheet — the viewer's toolbar shows the real number)
- `title=` — toolbar label; encode spaces as `%20`
- `height` — 720 works well; drop to ~560 if the lesson feels cramped on mobile

---

## Starter rows for your cheat sheet

| Lesson topic | File | Printed | `page=` |
|---|---|---|---|
| Carburetor systems | phak-ch07.pdf | 7-8 | 8 |
| Carburetor icing | phak-ch07.pdf | 7-9 | 9 |
| Carburetor heat | phak-ch07.pdf | 7-10 | 10 |

Add rows as you build lessons — send me a list of lesson topics and I'll fill in the file/page columns for the whole course.
