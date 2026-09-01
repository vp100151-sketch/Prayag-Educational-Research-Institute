# Prayag Educational Research Institute — Website

> **📌 UPDATE NOTE #2 (launch se pehle ka update):**
> - **Homepage banner** ab poori tarah **book cover jaisa** dikhta hai —
>   cream background, navy border, orange corner accents, shlok line,
>   diya emblem — sab kuch cover page ke design se match karta hai
>   (pehle ek alag dark-navy banner image thi, ab woh cover-style
>   coded banner ban gayi hai, isliye kisi bhi screen size par sharp
>   dikhegi).
> - **CA Intermediate (IPCC) aur CA Final** homepage par jod diye
>   gaye hain — "अपना Course चुनिए" section me ab teen tabs hain:
>   **Foundation / Intermediate (IPCC) / Final**. Foundation Paper 1
>   (Accounting) abhi live hai; Inter ke 6 aur Final ke 6 papers list
>   me dikhte hain "जल्द आ रहा है" tag ke saath — jaise-jaise unki PDF
>   taiyar ho, `js/data.js` ke `LEVELS` array me bas unka `bookId`
>   bhar dijiye (neeche "Naya chapter kaise add karein" section me
>   tareeka same hai).
> - Homepage ke feature-cards me 3 naye cards jode gaye hain jo
>   already-working features ko highlight karte hain: Topic-wise
>   प्रश्न बैंक search, ⭐ महत्वपूर्ण question marking, aur अपनी
>   Progress track karna.
> - Sabhi pages (about/contact/book/qbank) ka footer aur about.html
>   ka copy ab "Foundation, Intermediate (IPCC) aur Final" bolta hai,
>   sirf Foundation nahi.

> **📌 UPDATE NOTE (is version me kya badla):**
> Yeh website do purani zip files (`Prayag_CA_StudyPartner_2019_FullUpdated` aur
> `prayag-ca-website-updated`) ko compare karke, dono ka best content ek saath
> merge karke banayi gayi hai:
> - Dono files ke Question Bank (`js/qbank-data.js`) ko **union** kiya gaya —
>   koi bhi sawaal chhoota nahi (178 total sawaal, pehle 109 aur 115 the).
> - Jahan ek hi sawaal dono me tha, wahaan **naye/updated version** (jisme
>   fullscreen modal, PDF download, question/answer-only view jaisi advanced
>   features the) ko rakha gaya — kyunki wahi zyada polished tha.
> - **Chapter 10 — "कंपनी खातों का परिचय / Introduction to Company Accounts"**
>   me 6 naye, poori tarah verify kiye hue sawaal-jawab jode gaye hain (Rights
>   Issue, Bonus Shares, Forfeiture & Reissue, Pro-rata Allotment, Debenture
>   Redemption) — inki calculation ki galtiyaan (General Reserve over-utilise
>   hona, galat multiplication, etc.) pehle dhoondh kar theek ki gayi thi.
> - Ek stray/junk folder (`{css,js,assets,pdfs...}` naam ka, galti se bane
>   raw braces wala empty folder) hata diya gaya.
> - "Screen full" / fullscreen reading feature already updated site me maujood
>   hai (question kholte hi browser ka apna Fullscreen mode chalu ho jaata hai,
>   saath me "केवल प्रश्न / केवल उत्तर / दोनों" view switch bhi hai).


CA Foundation ke Hindi medium students ke liye chapter-wise study material
website. Yeh ek **static website** hai — matlab isko chalane ke liye kisi
server, database ya coding knowledge ki zaroorat nahi. Sirf yeh files kisi
bhi free hosting par daal dijiye aur website live ho jaayegi.

## Folder ka structure

```
ca-website/
├── index.html          → Homepage
├── book.html            → Chapter list wala page (sabhi papers ke liye same page)
├── about.html            → About / hamare baare me
├── contact.html          → Contact page
├── css/style.css         → Poora design isi ek file me hai
├── js/data.js             → *** SABSE ZAROORI FILE *** — yahan chapters/books jodiye
├── js/main.js              → Website ka logic (isko chhedne ki zaroorat nahi)
├── assets/                  → Logo aur cover images
└── pdfs/
     └── paper1-accounting/  → Is paper ke sabhi chapter PDFs yahan rakhiye
```

## Naya chapter kaise add karein (sabse zaroori kaam)

1. Apni chapter ki PDF file `pdfs/paper1-accounting/` folder me daaliye.
2. `js/data.js` file kholiye (kisi bhi text editor me, jaise Notepad).
3. Us book ke `chapters` array me neeche ek naya entry jodiye:

```js
{
  no: 11,
  titleHindi: "आपका चैप्टर नाम",
  titleEnglish: "Your Chapter Name",
  pdf: "pdfs/paper1-accounting/chapter-11-your-file-name.pdf"
}
```

4. Save kariye. Website reload karte hi naya chapter list me dikhne lagega —
   koi aur file badalne ki zaroorat nahi.

**Zaroori baat:** `pdf` field me file ka naam bilkul waisa hi likhiye jaisa
aapne PDF file ka naam rakha hai (spelling, capital/small letters sab match
hone chahiye).

## Naya Paper/Book kaise add karein (jaise Paper 2 — Business Laws)

1. `pdfs/` ke andar ek naya folder banaiye, jaise `pdfs/paper2-law/`.
2. Uss book ka cover image `assets/` folder me daaliye.
3. `js/data.js` file me `BOOKS` array ke andar ek naya poora object jodiye
   (file ke neeche ek udaharan/example comment ke roop me diya gaya hai —
   usko copy karke apni details bhar dijiye).
4. Save kariye — naya paper apne aap homepage par card ke roop me dikhega.

## "अपना Course चुनिए" section kaise update karein (Foundation/Inter/Final)

Homepage par teen course-tabs (Foundation, Intermediate · IPCC, Final)
aur unke paper-cards `js/data.js` ke `LEVELS` array se aate hain — har
level (jaise `{ id: "final", ... }`) ke andar uska apna `papers` array
hai. Jab tak kisi paper ki material taiyar nahi hai, uska `bookId: null`
rakhiye — card par "जल्द आ रहा है" dikhega. Jaise hi wo paper `BOOKS`
array me add ho jaaye, us paper ka `bookId` us book ke `id` se match
kar dijiye — card apne aap "Available" ho jaayega aur click karne par
seedha uske chapters khulenge.

Naya level (jaise koi future course) jodna ho to `LEVELS` array me
poora ek naya object (`id`, `nameHindi`, `nameEnglish`, `papers`)
jodiye — homepage par apne aap ek naya tab ban jaayega.

## Testimonials (student feedback) kaise jodein

`js/data.js` ke `TESTIMONIALS` array me abhi placeholder entries hain.
Jab real students se feedback mile, unhe wahan real naam aur real baat
se replace kar dijiye. Jab tak real feedback na ho, chahein to
`index.html` me poora `<section class="testimonials">` block hata
sakte hain.

## Search box

Homepage aur chapter-list page dono par ek search box hai jo turant
(bina reload kiye) paper/chapter ka naam filter karta hai — yeh
`js/data.js` ke data se hi kaam karta hai, kuch alag se set up nahi
karna padta.

## प्रश्न बैंक (Question Bank) — RTP/MTP/Paper master index

`js/qbank-data.js` file ek master index hai — bilkul jaise koi
spreadsheet ho: har row me Topic, Source (RTP/MTP/Paper), Year,
Q.No, Marks, poora Sawaal aur Uttar (Hindi me). Website par yeh
ek table ke roop me dikhta hai — topic/source/year se filter kar
sakte hain, aur kisi bhi row par click karke poora sawaal-uttar
padh sakte hain।

**Naya sawaal jodne ke steps:**
1. `js/qbank-data.js` kholiye.
2. `QUESTION_BANK` array me ek naya object jodiye — file ke andar
   hi neeche udaharan diya gaya hai (comment ke roop me), use copy
   karke apni details bhar dijiye.
3. `topicHindi`/`topicEnglish` wahi likhiye jo us sawaal ka ASLI
   chapter/topic hai (jaise "मूल्यह्रास") — isi naam se saalon ke
   sawaal apne aap ek saath group ho jaate hain, chahe kisi bhi
   paper me unka Q.No kuch bhi ho.
4. Agar answer abhi taiyar nahi hai, to `answerHindi: null` rakh
   dijiye — site par "उत्तर जल्द जोड़ा जाएगा" dikhega, sawaal phir
   bhi list me dikhega.

**Bade data (100+ rows) ke liye:** Haath se JS file editing mushkil
ho jaati hai itne data ke saath. Behtar hai ek Google Sheet/Excel
banaiye (columns: topicHindi, topicEnglish, chapterNo, source, year,
qno, marks, questionHindi, answerHindi), aur jab wo taiyar ho jaaye
to humein bataiye — hum website me ek CSV-loader jod denge taaki
aapko har baar coding na karni pade, sirf Sheet update karni pade.

**Student experience:** Har sawaal ke saath "महत्वपूर्ण" (star mark),
"पढ़ लिया गया" (read tracking), apne notes likhne ki jagah, aur
"अगला प्रश्न" button hai — yeh sab jaankari student ke apne browser
me hi save hoti hai (koi login/server nahi chahiye), taaki wo apni
practice track kar sake.

⚠️ **Zaroori salaah:** RTP/MTP/Question Papers ICAI ki apni
copyrighted samagri hain। Inhe website par daalna aam baat hai
(coaching institutes aksar karte hain), lekin behtar rahega ki:
(1) har jagah "Source: ICAI RTP/MTP" jaisa credit likha rahe,
(2) jahan tak ho sake, uttar apne author (Vishnu Prabhakar
Upadhayay ji) ke apne shabdon me likhe jaayein, ICAI ke suggested
answers ki hoo-ba-hoo copy na ho — isse students ko behtar samajh
bhi milegi aur copyright risk bhi kam hoga। Yeh ek business/legal
faisla hai jo aapko khud lena hoga — main koi lawyer nahi hoon,
lekin yeh dhyan rakhne wali baat zaroor hai।

## Website free me kaise live karein (koi cost nahi)

Sabse aasan tareeka — **Netlify Drop**:

1. Browser me [app.netlify.com/drop](https://app.netlify.com/drop) kholiye.
2. Is poore `ca-website` folder ko waha drag-and-drop kar dijiye.
3. Kuch second me aapko ek free website link mil jaayega
   (jaise `https://your-site-name.netlify.app`).
4. Baad me content update karna ho to phir se folder drag-drop kar dijiye,
   ya Netlify ko GitHub se jod kar automatic update kar sakte hain.

Doosra free option — **GitHub Pages**: is folder ko ek GitHub repository me
upload kariye, phir repository ki Settings → Pages me jaakar "Deploy from
branch" chuniye. Dono options bilkul free hain, koi credit card nahi
chahiye.

## Contact details kahan badlein

Phone number aur WhatsApp link har page ke footer me aur `contact.html` me
hai — inhe seedha HTML files me dhoondh kar (`+917007920430` search kariye)
apna number daal dijiye.

## Kisi cheez me atak jaayein to

`js/data.js` file hi wo jagah hai jahan 90% updates (naye chapters, naye
papers) ho jaate hain. Baaki files ko chhedne ki zaroorat aam taur par nahi
padegi.
