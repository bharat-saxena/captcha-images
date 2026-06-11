# 🔐 captcha-images

A structured dataset of **120 CAPTCHA images** paired with their text codes, organized into groups and available via raw GitHub URLs. Ideal for testing CAPTCHA validation systems, OCR training, UI prototyping, and form testing. But you can also it for mini and personal projects.

---

## 📁 Repository Structure

```
captcha-images/
├── a/                  # captcha_1.jpg  – captcha_10.jpg
├── b/                  # captcha_11.jpg – captcha_20.jpg
├── c/                  # captcha_21.jpg – captcha_30.jpg
├── d/                  # captcha_31.jpg – captcha_40.jpg
├── e/                  # captcha_41.jpg – captcha_50.jpg
├── f/                  # captcha_51.jpg – captcha_60.jpg
├── g/                  # captcha_61.jpg – captcha_70.jpg
├── h/                  # captcha_71.jpg – captcha_80.jpg
├── i/                  # captcha_81.jpg – captcha_90.jpg
├── j/                  # captcha_91.jpg – captcha_100.jpg
├── k/                  # captcha_101.jpg – captcha_110.jpg
├── l/                  # captcha_111.jpg – captcha_120.jpg
├── captcha_codes.txt   # Plain text list of all 120 CAPTCHA codes (one per line)
└── captcha_def.json    # JSON mapping of image URLs → text codes
```

---

## 🗂️ Group Index

Each folder (group) contains exactly **10 CAPTCHA images**.

| Group | Folder | Image Range         |
|-------|--------|---------------------|
| 1     | `a`    | captcha_1 – captcha_10   |
| 2     | `b`    | captcha_11 – captcha_20  |
| 3     | `c`    | captcha_21 – captcha_30  |
| 4     | `d`    | captcha_31 – captcha_40  |
| 5     | `e`    | captcha_41 – captcha_50  |
| 6     | `f`    | captcha_51 – captcha_60  |
| 7     | `g`    | captcha_61 – captcha_70  |
| 8     | `h`    | captcha_71 – captcha_80  |
| 9     | `i`    | captcha_81 – captcha_90  |
| 10    | `j`    | captcha_91 – captcha_100 |
| 11    | `k`    | captcha_101 – captcha_110|
| 12    | `l`    | captcha_111 – captcha_120|

---

## 🌐 Image URL Format

All images are directly accessible via raw GitHub URLs:

```
https://raw.githubusercontent.com/bharat-saxena/captcha-images/refs/heads/main/{group}/captcha_{n}.jpg
```

**Examples:**

```
# First image (group a, captcha 1)
https://raw.githubusercontent.com/bharat-saxena/captcha-images/refs/heads/main/a/captcha_1.jpg

# Eleventh image (group b, captcha 11)
https://raw.githubusercontent.com/bharat-saxena/captcha-images/refs/heads/main/b/captcha_11.jpg

# Last image (group l, captcha 120)
https://raw.githubusercontent.com/bharat-saxena/captcha-images/refs/heads/main/l/captcha_120.jpg
```

---

## 📄 Data Files

### `demo captcha`

![Captcha_1](https://raw.githubusercontent.com/bharat-saxena/captcha-images/refs/heads/main/a/captcha_1.jpg)
![Captcha_12](https://raw.githubusercontent.com/bharat-saxena/captcha-images/refs/heads/main/a/captcha_12.jpg)
![Captcha_29](https://raw.githubusercontent.com/bharat-saxena/captcha-images/refs/heads/main/a/captcha_29.jpg)
![Captcha_37](https://raw.githubusercontent.com/bharat-saxena/captcha-images/refs/heads/main/a/captcha_37.jpg)
![Captcha_43](https://raw.githubusercontent.com/bharat-saxena/captcha-images/refs/heads/main/a/captcha_43.jpg)
![Captcha_50](https://raw.githubusercontent.com/bharat-saxena/captcha-images/refs/heads/main/a/captcha_50.jpg)
![Captcha_65](https://raw.githubusercontent.com/bharat-saxena/captcha-images/refs/heads/main/a/captcha_65.jpg)
![Captcha_78](https://raw.githubusercontent.com/bharat-saxena/captcha-images/refs/heads/main/a/captcha_78.jpg)
![Captcha_86](https://raw.githubusercontent.com/bharat-saxena/captcha-images/refs/heads/main/f/captcha_86.jpg)
![Captcha_94](https://raw.githubusercontent.com/bharat-saxena/captcha-images/refs/heads/main/i/captcha_94.jpg)
![Captcha_101](https://raw.githubusercontent.com/bharat-saxena/captcha-images/refs/heads/main/d/captcha_101.jpg)
![Captcha_111](https://raw.githubusercontent.com/bharat-saxena/captcha-images/refs/heads/main/l/captcha_111.jpg)

### `captcha_codes.txt`

A plain text file with one CAPTCHA code per line, in order from captcha_1 to captcha_120.

```
RBSKW
TSMS9
R84CH
...
CE6JKS
```

### `captcha_def.json`

A JSON array mapping each image's direct URL to its corresponding text code. This is the primary file for integration.

```json
[
  {
    "image_url": "https://raw.githubusercontent.com/bharat-saxena/captcha-images/refs/heads/main/a/captcha_1.jpg",
    "text_code": "RBSKW"
  },
  {
    "image_url": "https://raw.githubusercontent.com/bharat-saxena/captcha-images/refs/heads/main/a/captcha_2.jpg",
    "text_code": "TSMS9"
  },
  ...
  {
    "image_url": "https://raw.githubusercontent.com/bharat-saxena/captcha-images/refs/heads/main/l/captcha_120.jpg",
    "text_code": "CE6JKS"
  }
]
```

---

## 🚀 Usage Examples

### Fetch a single image (JavaScript)

```javascript
const imageUrl = "https://raw.githubusercontent.com/bharat-saxena/captcha-images/refs/heads/main/a/captcha_1.jpg";

const img = document.createElement("img");
img.src = imageUrl;
document.body.appendChild(img);
```

### Load all CAPTCHA definitions (JavaScript)

```javascript
const response = await fetch(
  "https://raw.githubusercontent.com/bharat-saxena/captcha-images/refs/heads/main/captcha_def.json"
);
const captchas = await response.json();

// Pick a random captcha
const random = captchas[Math.floor(Math.random() * captchas.length)];
console.log(random.image_url);   // Image URL
console.log(random.text_code);   // Expected answer
```

### Validate user input (JavaScript)

```javascript
function validateCaptcha(userInput, expectedCode) {
  return userInput.trim().toUpperCase() === expectedCode.toUpperCase();
}

const captcha = captchas[0]; // { image_url: "...", text_code: "RBSKW" }
const userAnswer = document.getElementById("captcha-input").value;

if (validateCaptcha(userAnswer, captcha.text_code)) {
  console.log("✅ Correct!");
} else {
  console.log("❌ Incorrect. Please try again.");
}
```

### Load in Python

```python
import requests

url = "https://raw.githubusercontent.com/bharat-saxena/captcha-images/refs/heads/main/captcha_def.json"
captchas = requests.get(url).json()

for captcha in captchas[:5]:
    print(captcha["image_url"], "→", captcha["text_code"])
```

### Download all images (Python)

```python
import requests, os

captchas = requests.get(
    "https://raw.githubusercontent.com/bharat-saxena/captcha-images/refs/heads/main/captcha_def.json"
).json()

os.makedirs("captcha_downloads", exist_ok=True)

for i, captcha in enumerate(captchas, 1):
    img_data = requests.get(captcha["image_url"]).content
    filename = f"captcha_downloads/captcha_{i}_{captcha['text_code']}.jpg"
    with open(filename, "wb") as f:
        f.write(img_data)
    print(f"Saved: {filename}")
```

---

## 📊 Dataset Stats

| Property              | Detail                          |
|-----------------------|---------------------------------|
| Total images          | 120                             |
| Groups                | 12 (a – l)                     |
| Images per group      | 10                              |
| Image format          | JPG                             |
| Code length           | 4 – 6 characters               |
| Code character set    | Alphanumeric (A–Z, 0–9)        |

---

## 📌 Notes

- All CAPTCHA codes are **uppercase**. Validation should be case-insensitive to handle user input gracefully.
- Codes vary in length (4 to 6 characters) and may be purely alphabetic or alphanumeric.
- Image numbering is **sequential and global** — the number in the filename (e.g. `captcha_15`) directly maps to line 15 in `captcha_codes.txt`.

---

## 📜 License

This dataset is gathered from `https://captcha.com/demos`. Feel free to use it in your projects.

---

*Maintained by [@bharat-saxena](https://github.com/bharat-saxena)*
