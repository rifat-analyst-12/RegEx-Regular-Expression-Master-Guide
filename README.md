**Test: https://regex101.com/**


**RegEx** (Regular Expression বা রেগুলার এক্সপ্রেশন) হলো টেক্সট বা লেখা খোঁজার একটি **ডিজিটাল সার্চ টুল** বা বিশেষ সাংকেতিক ভাষা।

সহজ কথায় ধরো, তোমার কাছে ১,০০০ পৃষ্ঠার একটি বড় বই আছে। তুমি যদি সাধারণ `Ctrl + F` দিয়ে "করিম" নামটা খোঁজো, সে শুধু "করিম" লেখাটাই খুঁজে দেবে। কিন্তু তুমি যদি এমন কিছু খুঁজতে চাও যেমন:

* *"বইয়ের কোথায় কোথায় কোনো মোবাইল নম্বর (১১ টি সংখ্যা) আছে?"*
* *"কোথায় কোথায় একটি সঠিক ইমেইল আইডি লেখা আছে?"*
* *"যেসব শব্দ 'A' দিয়ে শুরু হয়েছে আর 'g' দিয়ে শেষ হয়েছে, সেগুলো বের করো।"*

এই ধরনের জটিল এবং বুদ্ধিমান সার্চ করার শর্টকাট ভাষাই হলো **RegEx**।

---

### ১. কীভাবে কাজ করে? (সবচেয়ে সহজ ৪টি চিহ্ন)

RegEx বোঝার জন্য পুরো ভাষা শেখার দরকার নেই, শুধু এই ৪টি চিহ্ন জানলেই আজকেই তুমি সার্চ করা শুরু করতে পারবে:

| চিহ্ন (Symbol) | নাম | কী কাজ করে? | উদাহরণ |
| --- | --- | --- | --- |
| **`\d`** | Digit (সংখ্যা) | যেকোনো **একটি** সংখ্যা (০-৯) খুঁজে বের করে। | `\d\d\d` দিয়ে ৩টি সংখ্যার জোট (যেমন: 123) খুঁজবে। |
| **`\w`** | Word (অক্ষর) | যেকোনো একটি বর্ণ, সংখ্যা বা আন্ডারস্কোর (_) খুঁজে নেয়। | `\w\w` দিয়ে পাশাপাশি ২টি অক্ষর খুঁজবে। |
| **`+`** | Plus (এক বা একাধিক) | আগের চিহ্নটি **এক বা একাধিকবার** থাকলে তা ধরে নেয়। | `\d+` দিয়ে ১টি বা তার বেশি যেকোনো দৈর্ঘ্যের সংখ্যা খুঁজে বের করবে। |
| **`.`** | Dot (যেকোনো কিছু) | নতুন লাইন ছাড়া যেকোনো একটি বর্ণ, সংখ্যা বা চিহ্নকে মেলায়। | `c.t` দিয়ে cat, cut, c9t সব খুঁজে পাবে। |

---

### ২. একটা রিয়েল-লাইফ উদাহরণ দেখি!

ধরো নিচের টেক্সট থেকে তোমাকে **ফোন নম্বরটি** খুঁজে বের করতে হবে:

> *"আমার ইমেইল test@gmail.com এবং আমার ফোন নম্বর 01712345678।"*

* তুমি যদি সার্চ বক্সে লেখো: **`\d+`**
* **RegEx কী করবে:** সে পুরো লেখাটা পড়ে যেখানেই পর পর সংখ্যা পাবে (এখানে `01712345678`), সেটাকে হাইলাইট করে ফেলবে!

---

### ৩. প্র্যাকটিস করার নিয়ম

আজকেই ট্রাই করে দেখার জন্য কোনো সফটওয়্যার ইনস্টল করতে হবে না:

1. ব্রাউজারে **regex101.com** ওয়েবসাইটে যাও।
2. **"TEST STRING"** বক্সে তোমার ইচ্ছামতো যেকোনো লেখা লিখে দাও।
3. **"REGULAR EXPRESSION"** বক্সে উপরে শেখা চিহ্নগুলো (যেমন: `\d+` বা `\w+`) লিখে দেখো নিচের লেখায় কী হাইলাইট হচ্ছে!



### ১. মূল বিল্ডিং ব্লক (মৌলিক প্রতীকসমূহ)

RegEx বোঝার সবচেয়ে সহজ উপায় হলো এর বিশেষ কিছু চিহ্নকে চেনা:

| চিহ্ন (Symbol) | নাম | কী কাজ করে? | উদাহরণ |
| --- | --- | --- | --- |
| **`\d`** | Digit (সংখ্যা) | যেকোনো **একটি** সংখ্যা (০-৯) খুঁজে বের করে। | `\d` দিয়ে `5` মিলবে। |
| **`\D`** | Non-digit | সংখ্যা ছাড়া অন্য যেকোনো বর্ণ বা চিহ্ন। | `\D` দিয়ে `A` বা `@` মিলবে। |
| **`\w`** | Word Character | যেকোনো বর্ণ (A-Z, a-z), সংখ্যা (0-9) বা আন্ডারস্কোর (_)। | `\w` দিয়ে `a`, `9`, `_` মিলবে। |
| **`\W`** | Non-word | বর্ণ/সংখ্যা/আন্ডারস্কোর ছাড়া সব (যেমন: স্পেস, @, #, $)। | `\W` দিয়ে `@` বা `!` মিলবে। |
| **`\s`** | Whitespace | যেকোনো স্পেস, ট্যাব (Tab) বা নতুন লাইন। | লেখার স্পেসগুলো খুঁজে পাবে। |
| **`.`** | Dot (যেকোনো কিছু) | নতুন লাইন ছাড়া যেকোনো একটি বর্ণ, সংখ্যা বা চিহ্ন। | `c.t` দিয়ে `cat`, `cut`, `c9t` মিলবে। |

---

### ২. কোয়ান্টিফায়ার (পরিমাণ নির্ধারণকারী চিহ্ন)

কোনো চিহ্ন কতবার থাকবে, তা বোঝাতে নিচের কোয়ান্টিফায়ারগুলো ব্যবহার করা হয়:

* **`+` (Plus):** ১ বা তার বেশিবার থাকা চাই। (যেমন: `\d+` দিয়ে পুরো সংখ্যা `1234` ধরা যাবে)।
* **`*` (Asterisk):** ০ বা তার বেশিবার (থাকতেও পারে, নাও থাকতে পারে বা একাধিকবার থাকতে পারে)।
* **`?` (Question Mark):** ০ বা ১ বার (ঐচ্ছিক/Optional)। যেমন: `colou?r` দিয়ে `color` এবং `colour` দুটিই মিলবে।
* **`{n}`:** ঠিক n বার। যেমন: `\d{4}` মানে ঠিক ৪টি সংখ্যা (যেমন: `2026`)।
* **`{n,m}`:** n থেকে m বার। যেমন: `\d{2,4}` মানে ২ থেকে ৪টি সংখ্যা।

---

### ৩. বাস্তব জীবনের ৪টি দারুণ উদাহরণ

#### উদাহরণ ১: বাংলাদেশি মোবাইল নম্বর ফিল্টার করা

* **সমস্যা:** একটি বড় ডকুমেন্টের ভেতর থেকে সব বাংলাদেশি ফোন নম্বর বের করতে হবে।
* **RegEx প্যাটার্ন:** `01[3-9]\d{8}`
* **কীভাবে কাজ করে?**
* `01` - নম্বরটি অবশ্যই `01` দিয়ে শুরু হবে।
* `[3-9]` - ৩ নম্বর ডিজিটটি ৩ থেকে ৯-এর মধ্যে হতে হবে (কারণ 010, 011 বা 012 সাধারণত অপারেটর কোড হয় না)।
* `\d{8}` - এরপর ঠিক ৮টি যেকোনো সংখ্যা থাকবে (মোট ১১ ডিজিট)।


* **যেগুলো মিলবে:** `01712345678`, `01987654321`

#### উদাহরণ ২: ইমেইল ঠিকানা (Email Address) ধরা

* **সমস্যা:** যেকোনো ইমেইল ফরম্যাট শনাক্ত করা।
* **RegEx প্যাটার্ন:** `[\w.-]+@[\w.-]+\.\w+`
* **কীভাবে কাজ করে?**
* `[\w.-]+` - `@`-এর আগে এক বা একাধিক অক্ষর, সংখ্যা, ডট বা হাইফেন।
* `@` - একটি আবশ্যক `@` চিহ্ন।
* `[\w.-]+` - ডোমেইনের নাম (যেমন: gmail, yahoo)।
* `\.` - ডোমেইনের পরের ডট (.) চিহ্ন।
* `\w+` - শেষের অংশ (যেমন: com, org, net)।


* **যেগুলো মিলবে:** `test.user_1@gmail.com`, `info@company.com.bd`

#### উদাহরণ ৩: তারিখ (Date Format) শনাক্ত করা

* **সমস্যা:** `15-08-2026` বা `15/08/2026` ফরম্যাটের তারিখ বের করা।
* **RegEx প্যাটার্ন:** `\d{2}[-/]\d{2}[-/]\d{4}`
* **কীভাবে কাজ করে?**
* `\d{2}` - ২ ডিজিটের দিন (যেমন: 15)।
* `[-/]` - একটি হাইফেন (`-`) অথবা একটি স্ল্যাশ (`/`) চিহ্ন।
* `\d{2}` - ২ ডিজিটের মাস (যেমন: 08)।
* `[-/]` - পুনরায় হাইফেন বা স্ল্যাশ।
* `\d{4}` - ৪ ডিজিটের বছর (যেমন: 2026)।



#### উদাহরণ ৪: স্ট্রং পাসওয়ার্ড যাচাইকরণ (Validation)

* **সমস্যা:** সাইটে রেজিস্ট্রেশনের সময় পাসওয়ার্ডটি নিরাপদ কি না চেক করা।
* **RegEx প্যাটার্ন:** `^(?=.*[a-z])(?=.*[A-Z])(?=.*\d).{8,}$`
* **কীভাবে কাজ করে?**
* `(?=.*[a-z])` - অন্তত ১টি ছোট হাতের অক্ষর থাকতে হবে।
* `(?=.*[A-Z])` - অন্তত ১টি বড় হাতের অক্ষর থাকতে হবে।
* `(?=.*\d)` - অন্তত ১টি সংখ্যা থাকতে হবে।
* `.{8,}` - মোট দৈর্ঘ্য সর্বনিম্ন ৮টি ক্যারেক্টার হতে হবে।



---

### ৪. স্থান নির্দিষ্ট করার চিহ্ন (Anchors)

* **`^` (Caret):** লাইনের **শুরু** বোঝায়। যেমন: `^Hello` (লাইনটি `Hello` দিয়ে শুরু হতে হবে)।
* **`$` (Dollar):** লাইনের **শেষ** বোঝায়। যেমন: `end$` (লাইনটি `end` দিয়ে শেষ হতে হবে)।
* **`\b` (Word Boundary):** নির্দিষ্ট কোনো শব্দকে আলাদাভাবে ধরে। যেমন: `\bcat\b` লিখলে শুধু "cat" মিলবে, "catfish" বা "concatenate"-এর ভেতরের "cat" মিলবে না।

---

### 💡 সহজে প্র্যাকটিস করার নিয়ম:

1. ব্রাউজারে **[regex101.com](https://regex101.com)** ওয়েবসাইটে যান।
2. **TEST STRING** বাক্সে আপনার পছন্দের যেকোনো টেক্সট লিখুন।
3. **REGULAR EXPRESSION** অংশে উপরের যেকোনো প্যাটার্ন (যেমন: `01[3-9]\d{8}`) বসিয়ে লাইভ টেস্ট করে দেখুন!



### ১. এডভান্সড কনসেপ্ট (গ্রুপিং ও ব্যাকরেফারেন্স)

এডভান্সড কাজগুলো করার জন্য এই প্রতীকগুলো অত্যন্ত কার্যকর:

| চিহ্ন / কৌশল | নাম | কাজ | উদাহরণ |
| --- | --- | --- | --- |
| **`( ... )`** | Capturing Group | নির্দিষ্ট অংশকে ব্র্যাকেটে ঘিরে গ্রুপ করা এবং মেমোরিতে ধরে রাখা। | `(\d{3})-(\d{4})` (কোড ও নম্বর আলাদা করা) |
| **`(?: ... )`** | Non-capturing Group | গ্রুপ করবে কিন্তু মেমোরিতে সেভ করবে না (পারফরম্যান্স ফাস্ট রাখতে)। | `(?:http|https)://` |
| **`\1, \2`** | Backreference | আগে ব্র্যাকেটে পাওয়া টেক্সটটি পুনরায় ব্যবহার করা। | `(\w+)\s+\1` (ডাবল শব্দ ধরা) |
| **`(?=...)`** | Positive Lookahead | সামনে নির্দিষ্ট কিছু থাকলে তবেই ম্যাচ করবে (কিন্তু সিলেক্ট করবে না)। | `\d+(?=\$ )` (ডলার চিহ্নের আগের সংখ্যা) |

---

### ২. বাস্তব জীবনের আরও ৫টি বাস্তব উদাহরণ

#### উদাহরণ ৫: URL / ওয়েবসাইট লিঙ্ক বের করা

* **লক্ষ্য:** যেকোনো `http://` বা `https://` ওয়েবসাইট লিঙ্ক খুঁজে বের করা।
* **RegEx প্যাটার্ন:** `https?://[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}(?:/\S*)?`
* **যেগুলো মিলবে:** `[https://google.com](https://google.com)`, `[http://my-site.org/about](http://my-site.org/about)`

#### उदाहरण ৬: IP Address (IPv4) ফিল্টার করা

* **লক্ষ্য:** নেটওয়ার্কের IP Address (যেমন: 192.168.1.1) ফিল্টার করা।
* **RegEx প্যাটার্ন:** `\b(?:\d{1,3}\.){3}\d{1,3}\b`
* **কীভাবে কাজ করে?**
* `\d{1,3}\.` - ১ থেকে ৩ ডিজিটের সংখ্যা এবং ডট (যেমন: 192.)।
* `{3}` - এই অংশটি পর পর ৩ বার রিপিট হবে (`192.168.1.`)।
* `\d{1,3}` - শেষে শুধু ১ থেকে ৩ ডিজিটের একটি সংখ্যা থাকবে (`1`)।



#### উদাহরণ ৭: HTML Tag মুছে ফেলা বা ধরা

* **লক্ষ্য:** HTML কোড থেকে ট্যাগগুলো বের করা (যেমন: `<h1>Header</h1>`)।
* **RegEx প্যাটার্ন:** `<[^>]+>`
* **যেগুলো মিলবে:** `<h1>`, `</div>`, `<img src="test.jpg" />`

#### উদাহরণ ৮: সোশ্যাল মিডিয়া হ্যাশট্যাগ ও মেশন

* **লক্ষ্য:** পোস্ট থেকে হ্যাশট্যাগ ও ইউজারনেম ফিল্টার করা।
* **Hashtag প্যাটার্ন:** `#\w+` (যেমন: `#bangladesh`, `#tech`)
* **Mention প্যাটার্ন:** `@\w+` (যেমন: `@user123`)

#### উদাহরণ ৯: টাইপিংয়ের ভুল বা ডুপ্লিকেট শব্দ ধরা

* **লক্ষ্য:** ভুলবশত পর পর দুবার লেখা একই শব্দ (যেমন: "This is **is** good") ধরা।
* **RegEx প্যাটার্ন:** `\b(\w+)\s+\1\b`
* **কীভাবে কাজ করে?** `(\w+)` ১ম শব্দটি মনে রাখে, এবং `\1` দিয়ে চেক করে পর পর ঠিক একই শব্দ আবার আছে কি না।

---

### ৩. টেক্সট রূপান্তর (Search & Replace Magic)

VS Code বা যেকোনো টেক্সট এডিটরে RegEx দিয়ে ফরম্যাট পরিবর্তনও করতে পারবেন:

* **আসল টেক্সট:** `01712-345678`
* **Search Pattern:** `(\d{5})-(\d{6})`
* **Replace Pattern:** `+880 $1 $2`
* **ফলাফল:** `+880 01712 345678`

---

### ৪. প্রোগ্রামিং কোডে ব্যবহার

**Python:**

```python
import re

text = "যোগাযোগ: info@example.com অথবা 01700000000"
emails = re.findall(r"[\w.-]+@[\w.-]+\.\w+", text)
phones = re.findall(r"01[3-9]\d{8}", text)

print(emails)  # ['info@example.com']
print(phones)  # ['01700000000']

```

**JavaScript:**

```javascript
const text = "অর্ডার আইডি: #ORD-99823";
const match = text.match(/#ORD-\d+/g);

console.log(match); // ["#ORD-99823"]

```


**JavaScript ES5** সংস্করণে RegEx (Regular Expression) ব্যবহারের জন্য মূলত **RegExp অবজেক্ট** এবং স্ট্রিং-এর বিল্ট-ইন মেথডগুলো ব্যবহার করা হয়। ES5 সংস্করণে RegEx-এর মৌলিক প্রায় সব মেথডই সহজলভ্য।

নিচে বিস্তারিতভাবে দেখানো হলো JavaScript ES5-এ আপনি কীভাবে কত উপায়ে RegEx ব্যবহার করতে পারেন:

---

### ১. RegEx তৈরি করার ২টি উপায় (ES5)

JavaScript ES5-এ রেগুলার এক্সপ্রেশন ২ ভাবে তৈরি করা যায়:

1. **Literal Syntax (সবচেয়ে জনপ্রিয় ও সহজ):**
```javascript
var pattern = /01[3-9]\d{8}/g;

```


2. **`RegExp` Constructor (ডাইনামিক প্যাটার্নের জন্য):**
```javascript
// যখন কোনো ভ্যারিয়েবল থেকে প্যাটার্ন বানাতে হয়
var searchKeyword = "gmail";
var pattern = new RegExp(searchKeyword, "i"); // "i" = Case insensitive

```



---

### ২. ES5-এ RegEx ব্যবহারের মূল মেথডসমূহ (Detailed Guide)

JavaScript-এ RegEx ব্যবহারের জন্য **২ ধরণের মেথড** রয়েছে:

* **RegExp Object-এর নিজের মেথড:** `test()`, `exec()`
* **String Object-এর মেথড:** `match()`, `replace()`, `search()`, `split()`

---

#### ক. `RegExp.prototype.test()` — সত্য না মিথ্যা যাচাই করতে

কোনো টেক্সটে আপনার প্যাটার্নটি আছে কি না তা যাচাই করার জন্য সবচেয়ে ফাস্ট মেথড এটি। এটি শুধু **`true`** বা **`false`** রিটার্ন করে।

* **ব্যবহারের ক্ষেত্র:** ইনপুট ভ্যালিডেশন (যেমন: ইমেইল বা ফোন নম্বর সঠিক আছে কি না)।

```javascript
var phonePattern = /^01[3-9]\d{8}$/;
var userInput = "01712345678";

if (phonePattern.test(userInput)) {
    console.log("সঠিক মোবাইল নম্বর!");
} else {
    console.log("ভুল মোবাইল নম্বর!");
}

```

---

#### খ. `String.prototype.match()` — মিল থাকা অংশগুলো খুঁজে বের করতে

টেক্সট থেকে প্যাটার্নের সাথে মিলে যাওয়া অংশগুলোকে একটি **Array (অ্যারে)** হিসেবে বের করে আনে।

* **গ্লোবাল ফ্ল্যাগ (`g`) ছাড়া:** প্রথম ম্যাচ করা টেক্সট ও তার ডিটেইলস দেখাবে।
* **গ্লোবাল ফ্ল্যাগ (`g`) সহ:** লেখার ভেতরের সব ম্যাচ করা টেক্সটের তালিকা দেবে।

```javascript
var text = "আমার ফোন 01712345678 এবং বন্ধুর ফোন 01887654321";
var pattern = /01[3-9]\d{8}/g;

var result = text.match(pattern);
console.log(result); 
// আউটপুট: ["01712345678", "01887654321"]

```

---

#### গ. `String.prototype.replace()` — খুঁজে নিয়ে বদলে ফেলা (Search & Replace)

টেক্সটের নির্দিষ্ট কোনো অংশ খুঁজে তা নতুন টেক্সট বা ফরম্যাট দিয়ে পরিবর্তন করার জন্য অত্যন্ত শক্তিশালী একটি মেথড।

**১. সহজ টেক্সট রিপ্লেস:**

```javascript
var str = "Welcome to 2020";
// সব সংখ্যাকে [NUMBER] দিয়ে বদলে ফেলা
var result = str.replace(/\d+/g, "[NUMBER]");
console.log(result); // "Welcome to [NUMBER]"

```

**২. Capturing Group ও Backreference ($1, $2) ব্যবহার করে ফরম্যাট পরিবর্তন:**

```javascript
// YYYY-MM-DD ফরম্যাটকে DD/MM/YYYY এ রূপান্তর
var dateStr = "2026-08-15";
var datePattern = /(\d{4})-(\d{2})-(\d{2})/;

var formattedDate = dateStr.replace(datePattern, "$3/$2/$1");
console.log(formattedDate); // "15/08/2026"

```

**৩. ফাংশন (Callback Function) ব্যবহার করে ডাইনামিক রিপ্লেস:**
ES5-এ `replace()` মেথডের ২য় আর্গুমেন্ট হিসেবে একটি ফাংশন পাস করা যায়:

```javascript
var prices = "আম ৫০ টাকা, জাম ১০০ টাকা";

// সব সংখ্যা ১০% বাড়িয়ে দেওয়া
var updatedPrices = prices.replace(/\d+/g, function(match) {
    var newPrice = parseInt(match) * 1.1;
    return newPrice;
});

console.log(updatedPrices); // "আম 55 টাকা, জাম 110 টাকা"

```

---

#### ঘ. `RegExp.prototype.exec()` — বিস্তারিত তথ্য সহ লুপ চালিয়ে ম্যাচ খোঁজা

`exec()` মেথডটি প্রতিটি ম্যাচের জন্য ইণ্ডেক্স (Index), ক্যাপচারিং গ্রুপ এবং টেক্সটের অবস্থান সহ বিস্তারিত তথ্য দেয়। এটি একটি লুপের ভেতর চালিয়ে একের পর এক ম্যাচ বের করা হয়।

```javascript
var text = "নম্বর: 101, কোড: 202, আইডি: 303";
var pattern = /\d+/g;
var match;

// যতক্ষণ ম্যাচ পাওয়া যাবে loop চলবে
while ((match = pattern.exec(text)) !== null) {
    console.log("পাওয়া গেছে: " + match[0] + " (অবস্থান: " + match.index + ")");
}
/* আউটপুট:
পাওয়া গেছে: 101 (অবস্থান: 7)
পাওয়া গেছে: 202 (অবস্থান: 18)
পাওয়া গেছে: 303 (অবস্থান: 28)
*/

```

---

#### ঙ. `String.prototype.search()` — অবস্থান বা Index বের করতে

কোনো প্যাটার্ন টেক্সটের **কত নম্বর ইনডেক্সে (Position)** শুরু হয়েছে তা বের করে। না পাওয়া গেলে `-1` দেয়। (এটি সাধারণ `indexOf()` এর মতো, কিন্তু এখানে RegEx ব্যবহার করা যায়)।

```javascript
var text = "Hello World! Learn JavaScript";
// প্রথম বড় হাতের শব্দ কোথায় আছে
var index = text.search(/[A-Z]/);

console.log(index); // 0 (কারণ 'H' প্রথম পজিশনে আছে)

```

---

#### চ. `String.prototype.split()` — RegEx দিয়ে টেক্সট টুকরো টুকরো করা

সাধারণত `split(",")` দিয়ে নির্দিষ্ট কমা অনুযায়ী লেখা ভাগ করা যায়। কিন্তু একাধিক স্পেস, কমা বা সেমিকোলন দিয়ে একত্রে ভাগ করতে RegEx `split()` অসাধারণ।

```javascript
var rawData = "রহিম, করিম;সাকিব   হাসান";

// কমা (,), সেমিকোলন (;) অথবা এক বা একাধিক স্পেস (\s+) দিয়ে ভাগ করা
var names = rawData.split(/[,;\s]+/);

console.log(names); 
// আউটপুট: ["রহিম", "করিম", "সাকিব", "হাসান"]

```

---

### ৩. ES5-এ ব্যবহৃত চার ধরনের ফ্ল্যাগ (Flags)

JavaScript ES5-এ RegEx-এর ৪টি মৌলিক ফ্ল্যাগ রয়েছে যা প্যাটার্নের শেষে বসে:

1. **`g` (Global):** প্রথম মিল পাওয়ার পরও না থেমে পুরো টেক্সটে যতগুলো মিল আছে সব খোঁজে।
2. **`i` (Ignore Case):** ছোট হাতের বা বড় হাতের বর্ণ (Case sensitivity) গ্রাহ্য করে না। (যেমন: `/hello/i` দিয়ে `Hello`, `HELLO` সব মিলবে)।
3. **`m` (Multiline):** বহুলাইনের ক্ষেত্রে `^` এবং `$` কে প্রতিটি লাইনের শুরু ও শেষ হিসেবে কাজ করায়।
4. **`y` (Sticky - ES5/ES6 transitional):** নির্দিষ্ট ইনডেক্স থেকে ঠিক পরের অংশ মেলানোর জন্য।

---

### summary: ES5 RegEx ব্যবহার করার কুইক চিটশিট

| মেথড | ইনপুট টাইপ | আউটপুট টাইপ | ব্যবহারের উদ্দেশ্য |
| --- | --- | --- | --- |
| **`pattern.test(str)`** | String | `Boolean` (true/false) | শুধুমাত্র শর্ত ঠিক আছে কি না তা যাচাই করা। |
| **`str.match(pattern)`** | RegEx | `Array` / `null` | মিলে যাওয়া অংশগুলোর তালিকা পাওয়া। |
| **`str.replace(pattern, newStr)`** | RegEx + String/Fn | `String` | খুঁজে বের করে রূপান্তর বা পরিবর্তন করা। |
| **`pattern.exec(str)`** | String | `Array` (With details) | প্রতিটি ম্যাচের ইনডেক্স ও গ্রুপ ডিটেইলস লুপে পাওয়া। |
| **`str.search(pattern)`** | RegEx | `Number` (Index) | প্যাটার্নটির শুরুর অবস্থান জানা। |
| **`str.split(pattern)`** | RegEx | `Array` | জটিল চিহ্নের ভিত্তিতে টেক্সট কেটে অ্যারে বানানো। |

---

**ওয়েব অ্যানালিটিক্স** (যেমন: Google Analytics 4, Adobe Analytics) এবং ডেটা অ্যানালিটিক্সে (Pandas, Python, JS-based Data Cleaning) **রেগুলার এক্সপ্রেশন (RegEx)** একটি অপরিহার্য হাতিয়ার।

অ্যানালিটিক্সে ডেটা প্রায়শই অগোছালো (Unstructured / Messy) থাকে। যেমন: URL থেকে ট্র্যাকিং আইডি বা কুয়েরি প্যারামিটার আলাদা করা, ইমেইল বা ফোন নম্বর মাস্ক করা, সেনসিটিভ তথ্য বাদ দেওয়া, ডোমেইন নেম ফিল্টার করা ইত্যাদি কাজে RegEx সবচেয়ে বেশি সাহায্য করে।

নিচে ওয়েব ও ডেটা অ্যানালিটিক্সে ব্যবহৃত **৫টি রিয়েল-লাইফ কেস স্টাডি** এবং সেগুলোর **JavaScript (ES5)** ও **Python** কোড উদাহরণ দিয়ে ব্যাখ্যা করা হলো:

---

### কেস ১: URL থেকে UTM / Query Parameters কেটে পরিষ্কার করা (Data Cleaning)

**সমস্যা:** ওয়েব অ্যানালিটিক্সে ইউজাররা যখন ক্যাম্পেইন ট্র্যাকিং লিঙ্ক (`?utm_source=facebook&utm_medium=cpc`) দিয়ে ওয়েবসাইটে আসে, তখন ডাটাবেজে একই পেজের URL শত শত ভিন্ন ভিন্ন লাইনে জমা হয়। অ্যানালিটিক্স রিপোর্টে ক্লিন পেজ প্যাথ বের করতে কুয়েরি প্যারামিটার বাদ দেওয়া প্রয়োজন।

* **JavaScript (ES5):**

```javascript
// অ্যানালিটিক্স ট্র্যাকিং স্ক্রিপ্টে পেজ URL ক্লিন করা
var rawUrl = "https://example.com/products/phone?utm_source=facebook&utm_campaign=summer_sale";

// '?' এবং এর পরের সব অংশ মুছে ফেলা
var cleanUrl = rawUrl.replace(/\?.*$/, "");

console.log(cleanUrl); 
// আউটপুট: "https://example.com/products/phone"

```

* **Python (Pandas / Analytics Pipeline):**

```python
import re

raw_url = "https://example.com/products/phone?utm_source=facebook&utm_campaign=summer_sale"

# RegEx দিয়ে '?' থেকে শুরু করে বাকী অংশ সরিয়ে ফেলা
clean_url = re.sub(r'\?.*$', '', raw_url)

print(clean_url)
# আউটপুট: "https://example.com/products/phone"

```

---

### কেস ২: ইউজার বিহেভিয়ার ডাটা থেকে নির্দিষ্ট প্রোডাক্ট ক্যাটাগরি ফিল্টার করা (Segmentation)

**সমস্যা:** আপনার কাছে হাজার হাজার ইউজার ক্লিক বা পেজ ভিউ ডাটা আছে। আপনি শুধু `/category/electronics/` বা `/category/fashion/` এর মত নির্দিষ্ট সেগমেন্টের পেজ ট্রাফিক আলাদা করতে চান।

* **JavaScript (ES5):**

```javascript
var pagePaths = [
  "/home",
  "/category/electronics/phone-123",
  "/about-us",
  "/category/fashion/shirt-456"
];

// ক্যাটাগরি পেজ সনাক্ত করার নিয়ম
var categoryPattern = /^\/category\/([^\/]+)\//;

for (var i = 0; i < pagePaths.length; i++) {
  var match = pagePaths[i].match(categoryPattern);
  if (match) {
    console.log("ক্যাটাগরি পেজ: " + pagePaths[i] + " | প্রধান ক্যাটাগরি: " + match[1]);
  }
}
/* আউটপুট: 
   ক্যাটাগরি পেজ: /category/electronics/phone-123 | প্রধান ক্যাটাগরি: electronics
   ক্যাটাগরি পেজ: /category/fashion/shirt-456 | প্রধান ক্যাটাগরি: fashion
*/

```

* **Python (Data Analysis with Pandas):**

```python
import pandas as pd

# অ্যানালিটিক্স লগ ডাটাফ্রেম
data = {'PagePath': ['/home', '/category/electronics/phone-123', '/about-us', '/category/fashion/shirt-456']}
df = pd.DataFrame(data)

# RegEx ফিল্টার: শুধুমাত্র /category/ যুক্ত পেজগুলো বের করা
category_df = df[df['PagePath'].str.contains(r'^/category/', regex=True)]

print(category_df)
'''
আউটপুট:
                         PagePath
1  /category/electronics/phone-123
3     /category/fashion/shirt-456
'''

```

---

### কেস ৩: প্রাইভেসি ও GDPR বজায় রাখতে সেনসিটিভ ডাটা মাস্ক করা (PII Anonymization)

**সমস্যা:** ইউজার বা অ্যানালিটিক্স লগে কখনো ভুলবশত ইউজারের মোবাইল নম্বর বা ইমেইল আইডি চলে আসলে তা অ্যানালিটিক্স প্ল্যাটফর্মে সেভ করা আইনগতভাবে অপরাধ (PII - Personally Identifiable Information Violation)। এটি মাস্ক করতে RegEx ব্যবহার করা হয়।

* **JavaScript (ES5):**

```javascript
var userLog = "ইউজার সমস্যা জানিয়েছেন, যোগাযোগ নম্বর 01712345678 এবং ইমেইল test@gmail.com";

// বাংলাদেশি মোবাইল নম্বর মাস্কিং (013-019XX...)
var maskedLog = userLog.replace(/01[3-9]\d{8}/g, "01XXXXXXXXX");

// ইমেইল মাস্কিং
maskedLog = maskedLog.replace(/([a-zA-Z0-9._-]+)@([a-zA-Z0-9._-]+)/g, "***@***.com");

console.log(maskedLog);
// আউটপুট: "ইউজার সমস্যা জানিয়েছেন, যোগাযোগ নম্বর 01XXXXXXXXX এবং ইমেইল ***@***.com"

```

* **Python:**

```python
import re

user_log = "ইউজার সমস্যা জানিয়েছেন, যোগাযোগ নম্বর 01712345678 এবং ইমেইল test@gmail.com"

# মোবাইল নম্বর ও ইমেইল এক সাথে পরিবর্তন
clean_log = re.sub(r'01[3-9]\d{8}', '01XXXXXXXXX', user_log)
clean_log = re.sub(r'[\w\.-]+@[\w\.-]+', '***@***.com', clean_log)

print(clean_log)
# আউটপুট: "ইউজার সমস্যা জানিয়েছেন, যোগাযোগ নম্বর 01XXXXXXXXX এবং ইমেইল ***@***.com"

```

---

### কেস ৪: রেফারার বা সোর্স থেকে ডোমেইন নেম এক্সট্র্যাক্ট করা (Traffic Source Attribution)

**সমস্যা:** অ্যানালিটিক্সে ইউজারের ফুল রেফারার URL (যেমন: `[https://l.facebook.com/l.php?u=](https://l.facebook.com/l.php?u=)...`) থেকে মূল প্ল্যাটফর্ম বা চ্যানেল (যেমন: `facebook.com`) আলাদা করা।

* **JavaScript (ES5):**

```javascript
var referrerUrl = "https://subdomain.google.com/search?q=javascript";

// মূল ডোমেইন আলাদা করার প্যাটার্ন
var domainPattern = /^(?:https?:\/\/)?(?:www\.)?([^\/]+)/i;
var result = referrerUrl.match(domainPattern);

if (result) {
  console.log("সোর্স ডোমেইন: " + result[1]);
}
// আউটপুট: "সোর্স ডোমেইন: subdomain.google.com"

```

* **Python:**

```python
import re

referrer_url = "https://subdomain.google.com/search?q=javascript"

# ডোমেইন এক্সট্র্যাক্ট
match = re.search(r'https?://(?:www\.)?([^/]+)', referrer_url)
if match:
    print("সোর্স ডোমেইন:", match.group(1))

# আউটপুট: "সোর্স ডোমেইন: subdomain.google.com"

```

---

### কেস ৫: ফর্ম ইনপুট এ্যারর বের করা (Conversion Rate Optimization / CRO)

**সমস্যা:** ওয়েব অ্যানালিটিক্সে ফর্ম জমা দেওয়ার সময় ইউজাররা কেন ব্যর্থ হচ্ছে তা ট্র্যাক করতে, ক্লায়েন্ট সাইড বা অ্যানালিটিক্স ট্যাগ ম্যানেজারে (Google Tag Manager) ইনপুট ভ্যালিডেশন চেক করতে হয়।

* **JavaScript (ES5 - GTM Custom JavaScript Variable এ ব্যবহৃত হয়):**

```javascript
// জিপ কোড (Zip Code) ঠিক আছে কি না যাচাই
var zipCode = "1216"; // ঢাকা মিরপুর জিপ কোড 
var bangladeshZipPattern = /^\d{4}$/; // ঠিক ৪টি সংখ্যা

function validateZip(code) {
  return bangladeshZipPattern.test(code);
}

console.log(validateZip(zipCode)); // true
console.log(validateZip("12165")); // false

```

* **Python:**

```python
import re

zip_codes = ["1216", "121", "12165", "DHAKA"]
valid_pattern = r'^\d{4}$'

valid_codes = [code for code in zip_codes if re.match(valid_pattern, code)]
print("সঠিক জিপ কোডসমূহ:", valid_codes)

# আউটপুট: সঠিক জিপ কোডসমূহ: ['1216']

```

---

### সারসংক্ষেপ:

* **JavaScript (ES5):** সাধারণত **Google Tag Manager (GTM)**, ডায়নামিক ট্র্যাকিং পিক্সেল, এবং ব্রাউজার সাইড ডাটা প্রসেসিং ও ইভেন্ট ট্র্যাকিংয়ের জন্য ব্যবহৃত হয়।
* **Python:** সাধারণত অ্যানালিটিক্স ডাটাবেইজ, **BigQuery**, **Pandas**, বা **ETL Pipeline**-এ লাখ লাখ অগোছালো ডাটা রিক্লিন বা প্রসেস করার ক্ষেত্রে ব্যবহৃত হয়।


---

ওয়েব ও ডেটা অ্যানালিটিক্সে রেগুলার এক্সপ্রেশনের (RegEx) আরও অনেকগুলো বাস্তবমুখী এবং অ্যাডভান্সড ব্যবহার রয়েছে।

নিচে **আরও ৪টি গুরুত্বপূর্ণ রিয়েল-লাইফ কেস স্টাডি**JavaScript (ES5) এবং Python কোডসহ ব্যাখ্যা করা হলো:

---

### কেস ৬: Google Tag Manager / Analytics-এ IP Anonymization & Filtering

**সমস্যা:** GDPR / প্রাইভেসি নিয়মের কারণে ইউজারের পুরো IP অ্যাড্রেস (যেমন: `192.168.1.15`) অ্যানালিটিক্সে সেভ করা যায় না। শেষ অক্টেটটি `0` বানিয়ে সংবেদনশীল তথ্য বাদ দিতে হয়। অথবা কোম্পানির নিজস্ব অফিসের অভ্যন্তরীণ ট্রাফিক (Internal Traffic) ফিল্টার করে বাদ দিতে হয়।

* **JavaScript (ES5):**

```javascript
// IP Address এর শেষের অংশ ০ (Anonymize) করা
var userIP = "192.168.1.105";

// শেষের ৩টি সংখ্যাকে ০ দিয়ে রিপ্লেস করা
var anonymizedIP = userIP.replace(/\.\d+$/, ".0");

console.log(anonymizedIP); 
// আউটপুট: "192.168.1.0"

```

* **Python:**

```python
import re

user_ip = "192.168.1.105"

# RegEx দিয়ে শেষ অংশ সরিয়ে ০ বসানো
anonymized_ip = re.sub(r'\.\d+$', '.0', user_ip)

print(anonymized_ip)
# আউটপুট: "192.168.1.0"

```

---

### কেস ৭: সার্চ কনসোল ও অ্যানালিটিক্স থেকে "Long-tail" এবং "Brand Keywords" আলাদা করা

**সমস্যা:** SEO ও অ্যানালিটিক্স ডেটায় ব্যবহারকারীরা কী লিখে সার্চ করছে তা আলাদা করা প্রয়োজন। যেমন: ব্র্যান্ড নেম (যেমন: "Daraz") যুক্ত সার্চ বনাম নন-ব্র্যান্ড বা লং-টেইল কুয়েরি (যেমন: "best smartphone under 20000") আলাদা করা।

* **JavaScript (ES5):**

```javascript
var searchQueries = [
  "daraz online shopping",
  "best laptop price in bd",
  "daraz discount coupon",
  "mobile phone offer"
];

// 'daraz' কথাটি আছে কি না চেক করা (Case insensitive)
var brandPattern = /daraz/i;

for (var i = 0; i < searchQueries.length; i++) {
  if (brandPattern.test(searchQueries[i])) {
    console.log("Brand Query: " + searchQueries[i]);
  } else {
    console.log("Non-Brand Query: " + searchQueries[i]);
  }
}

```

* **Python (Data Analytics in Pandas):**

```python
import pandas as pd

queries = ["daraz online shopping", "best laptop price in bd", "daraz discount coupon", "mobile phone offer"]
df = pd.DataFrame({'SearchQuery': queries})

# ব্র্যান্ড কুয়েরির জন্য নতুন কলাম তৈরি
df['QueryType'] = df['SearchQuery'].apply(lambda x: 'Brand' if re.search(r'daraz', x, re.I) else 'Non-Brand')

print(df)
'''
আউটপুট:
               SearchQuery QueryType
0    daraz online shopping     Brand
1  best laptop price in bd Non-Brand
2    daraz discount coupon     Brand
3       mobile phone offer Non-Brand
'''

```

---

### কেস ৮: ডিভাইস এবং ব্রাউজার ইউজার এজেন্ট (User-Agent) থেকে তথ্য বের করা

**সমস্যা:** সার্ভার লগে ইউজারের ইউজার-এজেন্ট স্ট্রিং (যেমন: `Mozilla/5.0 (iPhone; CPU iPhone OS 15_0...`) থাকে। সেখান থেকে ইউজার **iPhone**, **Android** নাকি **Windows** ব্যবহার করছে তা সনাক্ত করা।

* **JavaScript (ES5):**

```javascript
var userAgent = "Mozilla/5.0 (iPhone; CPU iPhone OS 14_6 like Mac OS X) AppleWebKit/605.1.15";

function detectDevice(ua) {
  if (/iPhone|iPad|iPod/i.test(ua)) {
    return "iOS Device";
  } else if (/Android/i.test(ua)) {
    return "Android Device";
  } else if (/Windows/i.test(ua)) {
    return "Windows Desktop";
  }
  return "Unknown Device";
}

console.log(detectDevice(userAgent)); 
// আউটপুট: "iOS Device"

```

* **Python:**

```python
import re

user_agent = "Mozilla/5.0 (Linux; Android 11; SM-A505F) AppleWebKit/537.36"

if re.search(r'Android', user_agent, re.I):
    device = "Android"
elif re.search(r'iPhone|iPad', user_agent, re.I):
    device = "iOS"
else:
    device = "Other"

print("ডিভাইস টাইপ:", device)
# আউটপুট: "ডিভাইস টাইপ: Android"

```

---

### কেস ৯: ই-কমার্স অর্ডার আইডি (SKU / Order Code) ফরম্যাট ভ্যালিডেশন

**সমস্যা:** ই-কমার্স অ্যানালিটিক্সে ইভেন্ট ট্র্যাকিংয়ের সময় অর্ডার আইডি সঠিক ফরম্যাটে আছে কি না (যেমন: `ORD-2026-9876`) তা নিশ্চিত করা।

* **JavaScript (ES5):**

```javascript
// ফরম্যাট: "ORD-" এর পর ৪টি সংখ্যা, তারপর "-" এবং ৪টি সংখ্যা
var orderPattern = /^ORD-\d{4}-\d{4}$/;

var validOrder = "ORD-2026-4321";
var invalidOrder = "1234-ORD";

console.log(orderPattern.test(validOrder));   // true
console.log(orderPattern.test(invalidOrder)); // false

```

* **Python:**

```python
import re

order_ids = ["ORD-2026-4321", "ORD-123", "INVALID-9999", "ORD-2026-9999"]
pattern = r'^ORD-\d{4}-\d{4}$'

valid_orders = [o for o in order_ids if re.match(pattern, o)]

print("ভ্যালিড অর্ডার আইডি:", valid_orders)
# আউটপুট: ভ্যালিড অর্ডার আইডি: ['ORD-2026-4321', 'ORD-2026-9999']

```

---

### সংক্ষেপে

* **ওয়েব অ্যানালিটিক্স (GTM, JS):** রিয়েল-টাইমে পেজ ভিউ, কাস্টম ক্লিক, ইভেন্ট ট্র্যাকিং এবং প্রাইভেসি মাস্কিংয়ের কাজ সহজ করে।
* **ডেটা অ্যানালিটিক্স (Python, SQL):** অগোছালো ডাটাবেজ ক্লিওনিং, ক্লাসিফিকেশন, রিপোর্টিং ও সেগমেন্টেশনের কাজ অনেক দ্রুত সম্পন্ন করে।

---

এবার অ্যানালিটিক্সের একটু **অ্যাডভান্সড ও স্পেশালাইজড টেকনিক** দেখা যাক, যেগুলো বড় স্কেলের ডাটা প্রসেসিং, সিকিউরিটি এবং মেশিন লার্নিং ডাটা প্রিপারেশনের জন্য ব্যবহৃত হয়।

নিচে আরও **৪টি অ্যাডভান্সড কেস স্টাডি** JavaScript (ES5) এবং Python কোডসহ দেওয়া হলো:

---

### কেস ১০: SQL Injection ও Malicious Script আক্রমণ সনাক্তকরণ (Security Analytics)

**সমস্যা:** ওয়েব অ্যানালিটিক্স এবং লগে কিছু অসাধু অ্যাটাক ট্রাফিক জমা হয় (যেমন: `<script>` বা `UNION SELECT` ইনজেকশন)। ডাটা অ্যানালিটিক্স টিমের কাজ হলো ট্রাফিক ডাটা বিশ্লেষণ করে এই ক্ষতিকর প্যাটার্নগুলো ফ্ল্যাগ করা।

* **JavaScript (ES5):**

```javascript
var searchPayload = "laptop' UNION SELECT * FROM users--";

// সাধারণ SQL Injection প্যাটার্ন
var sqlInjectionPattern = /(\b(SELECT|INSERT|DELETE|DROP|UNION)\b)|('--)/i;

if (sqlInjectionPattern.test(searchPayload)) {
  console.log("সতর্কতা: ক্ষতিকর সার্চ কুয়েরি সনাক্ত হয়েছে!");
}

```

* **Python:**

```python
import re

logs = [
    "product_id=105",
    "search=<script>alert('hack')</script>",
    "user_id=12 OR 1=1"
]

# Script Injection বা SQLi সনাক্তকরণ
security_pattern = r"(<script>|UNION\s+SELECT|OR\s+1=1)"

flagged_logs = [log for log in logs if re.search(security_pattern, log, re.I)]
print("ফ্ল্যাগ করা লগের তালিকা:", flagged_logs)
# আউটপুট: ['search=<script>alert(\'hack\')</script>', 'user_id=12 OR 1=1']

```

---

### কেস ১১: সোশ্যাল মিডিয়া ট্রাফিক সেগমেন্টেশন (Custom Attribution)

**সমস্যা:** রেফারার লিঙ্কে Facebook-এর বিভিন্ন ভ্যারিয়েন্ট যেমন: `l.facebook.com`, `m.facebook.com`, `lm.facebook.com` বা `instagram.com` থাকতে পারে। এদের সবগুলোকে একসাথে "Social Media" সেগমেন্টে ক্যাটাগরাইজ করা।

* **JavaScript (ES5):**

```javascript
var referrer = "https://l.facebook.com/l.php?u=https://mysite.com";

// সোশ্যাল মিডিয়া ডোমেইন সনাক্তকরণ
var socialPattern = /(facebook|instagram|linkedin|twitter|t\.co|pinterest)/i;

function getTrafficChannel(ref) {
  if (socialPattern.test(ref)) {
    return "Social";
  }
  return "Other Channel";
}

console.log(getTrafficChannel(referrer)); // "Social"

```

* **Python:**

```python
import pandas as pd
import re

data = {'Referrer': ['https://m.facebook.com/', 'https://www.google.com/', 'https://t.co/xyz123']}
df = pd.DataFrame(data)

# RegEx দিয়ে চানেল ট্যাগ করা
df['Channel'] = df['Referrer'].apply(
    lambda x: 'Social' if re.search(r'(facebook|instagram|twitter|t\.co)', x, re.I) else 'Organic/Other'
)

print(df)

```

---

### কেস ১২: ই-কমার্স রিভিউ থেকে "রেটিং ও প্রাইস" এক্সট্রাকশন (Unstructured Data Analytics)

**সমস্যা:** স্ক্র্যাপ করা প্রোডাক্ট রিভিউ বা ফিডব্যাক ডাটা থেকে আনস্ট্রাকচার্ড টেক্সটের ভেতর থেকে প্রোডাক্ট প্রাইস (যেমন: `৳১৫০০` বা `$150`) এবং স্টার রেটিং বের করা।

* **JavaScript (ES5):**

```javascript
var reviewText = "প্রোডাক্টটি ভালো ছিল, দাম নিয়েছে ৳1250 টাকা। আমি এটাকে 4.5/5 দেব।";

// রেটিং এবং প্রাইস খুঁজে বের করা
var priceMatch = reviewText.match(/৳?\s?(\d+)/);
var ratingMatch = reviewText.match(/(\d(\.\d)?)\s?\/\s?5/);

if (priceMatch) console.log("দাম: " + priceMatch[1]);     // 1250
if (ratingMatch) console.log("রেটিং: " + ratingMatch[1]); // 4.5

```

* **Python:**

```python
import re

review_text = "Good product for $150. I give it 4.8/5 stars."

# ডলার বা মূল্যের পরিমাণ এক্সট্র্যাক্ট করা
price = re.search(r'\$\d+', review_text)
# রেটিং এক্সট্র্যাক্ট করা
rating = re.search(r'(\d\.\d)/\d', review_text)

if price: print("Price:", price.group(0))    # Price: $150
if rating: print("Rating:", rating.group(1)) # Rating: 4.8

```

---

### কেস ১৩: সেশন টাইম ফরম্যাট কনভার্সন (Log Analysis)

**সমস্যা:** সার্ভার লগে সেশন ডিউরেশন বা টাইমস্ট্যাম্প ভিন্ন ফরম্যাটে থাকে (যেমন: `02h 15m 30s` বা `135m`). একে সেকেন্ডে রূপান্তর করার জন্য সংখ্যাগুলো আলাদা করা প্রয়োজন।

* **JavaScript (ES5):**

```javascript
var duration = "02h 15m 30s";

// ঘন্টা, মিনিট ও সেকেন্ড আলাদা করার জন্য Capturing Group
var durationPattern = /(\d+)h\s*(\d+)m\s*(\d+)s/;
var match = duration.match(durationPattern);

if (match) {
  var hours = parseInt(match[1]);
  var minutes = parseInt(match[2]);
  var seconds = parseInt(match[3]);
  
  var totalSeconds = (hours * 3600) + (minutes * 60) + seconds;
  console.log("মোট সেশন টাইম (সেকেন্ডে): " + totalSeconds); // 8130
}

```

* **Python:**

```python
import re

duration = "02h 15m 30s"
match = re.search(r'(\d+)h\s*(\d+)m\s*(\d+)s', duration)

if match:
    hours, minutes, seconds = map(int, match.groups())
    total_seconds = hours * 3600 + minutes * 60 + seconds
    print("মোট সেশন টাইম (সেকেন্ডে):", total_seconds) # 8130

```

---

Google Tag Manager (GTM) এর কাস্টম ভ্যারিয়েন্ট কনফিগারেশন এবং BigQuery / SQL-এ RegEx ব্যবহারের প্র্যাকটিক্যাল গাইড দেওয়া হলো।

---

### ১. Google Tag Manager (GTM)-এ RegEx ও Custom JavaScript Variable

GTM-এ RegEx মূলত **Custom JavaScript (CJS)** ভ্যারিয়েন্ট তৈরি এবং **Triggers** কনফিগার করতে ব্যবহৃত হয়।

**সিনারিও:** ইউজার যখন কোনো ই-কমার্স পেজে থাকে, তখন URL থেকে SKU / Product ID বের করে ডেটালিয়ারে না পাঠালেও GTM-এর মাধ্যমে ট্র্যাকিং পিক্সেল পাঠানো।

**CJS Variable: "CJS - Extract Product SKU"**
GTM-এ `Custom JavaScript` সিলেক্ট করে নিচের ES5 কোডটি দেওয়া হয়:

```javascript
function() {
  // GTM Built-in Variable {{Page Path}}
  var path = {{Page Path}}; // উদাহরণ: "/p/electronics/samsung-galaxy-s24-SKU-998822"
  
  // SKU অংশ এক্সট্র্যাক্ট করার RegEx (SKU-এর পর থাকা ৬ ডিজিট)
  var match = path.match(/SKU-(\d{6})/i);
  
  if (match && match[1]) {
    return match[1]; // রিটার্ন করবে: "998822"
  }
  return "UNKNOWN_SKU";
}

```

**GTM Trigger Filtering Example:**
GTM ট্রিগারে সরাসরি RegEx Table বা Matches RegEx ব্যবহার করা যায়:

* **Trigger Type:** Page View
* **Condition:** `Page URL` -> `matches RegEx (ignore case)` -> `\/(checkout|cart|thank-you)\b`
* **কাজ:** এটি শুধু Checkout, Cart, বা Thank You পেজে ট্রিপ্রিগার অন করবে।

---

### ২. BigQuery / SQL-এ RegEx ব্যবহার (Large Scale Analytics)

BigQuery-তে লাখ লাখ ডাটার ওপর ফাস্ট কুয়েরি চালানোর জন্য RegEx ফাংশনগুলো (যেমন: `REGEXP_CONTAINS`, `REGEXP_EXTRACT`, `REGEXP_REPLACE`) ব্যবহৃত হয়।

#### কেস ১: `REGEXP_EXTRACT` দিয়ে URL থেকে Domain/Subdomain আলাদা করা

```sql
SELECT
  full_url,
  -- URL থেকে ডোমেইন এক্সট্র্যাক্ট করা
  REGEXP_EXTRACT(full_url, r'https?://([^/]+)') AS extracted_domain
FROM
  `your_project.analytics.page_views`
LIMIT 5;

```

#### কেস ২: `REGEXP_CONTAINS` দিয়ে ট্রাফিক সেগমেন্টেশন (Where Clause)

```sql
SELECT
  user_id,
  page_path,
  device_type
FROM
  `your_project.analytics.web_events`
WHERE
  -- শুধুমাত্র ব্লগ পোস্ট ও আর্টিকেলের পেজগুলো ফিল্টার করা
  REGEXP_CONTAINS(page_path, r'^/(blog|articles)/[a-z0-9-]+');

```

#### কেস ৩: `REGEXP_REPLACE` দিয়ে PII / Sensitive Data ক্লিন করা

```sql
SELECT
  user_feedback,
  -- ফিডব্যাক থেকে মোবাইল নম্বর জিরো (0) দিয়ে মাস্কিং করা
  REGEXP_REPLACE(user_feedback, r'01[3-9]\d{8}', '01XXXXXXXXX') AS anonymized_feedback
FROM
  `your_project.analytics.user_reviews`;

```

---

### BigQuery vs GTM RegEx-এর পার্থক্য

| বৈশিষ্ট্য | Google Tag Manager (GTM) | BigQuery / SQL |
| --- | --- | --- |
| **প্রসেসিং স্থান** | ক্লায়েন্ট সাইড (User Browser) | সার্ভার সাইড (Data Warehouse) |
| **ভাষা** | JavaScript (ES5 standard) | RE2 RegEx Engine (SQL Syntax) |
| **প্রয়োজনীয়তা** | রিয়েল-টাইম ডাটা ট্র্যাকিং ও ফিল্টারিং | ঐতিহাসিক ডাটা অ্যানালাইসিস ও ক্লিনআপ |

---

GTM (Google Tag Manager) এবং BigQuery/SQL-এ RegEx কীভাবে ব্যাকএন্ডে কাজ করে এবং কেন এদের ব্যবহারের পদ্ধতি ভিন্ন, তা সহজ ভাষায় বুঝিয়ে দেওয়া হলো।

---

### ১. GTM-এ RegEx যেভাবে কাজ করে

GTM মূলত ব্রাউজারে (User End) রিয়েল-টাইমে চলে। যখনই কোনো ইউজার ওয়েবসাইটে ক্লিক করে বা পেজ লোড করে, GTM-এর ভেতরে থাকা রেগুলার এক্সপ্রেশন সাথে সাথেই সিদ্ধান্ত নেয় ডাটা Google Analytics বা Facebook Pixel-এ পাঠাবে কি না।

* **CJS (Custom JavaScript Variable):** এটি একটি ছোট ফাংশন যা পেজের যেকোনো ডাটা (যেমন: URL, Click Text, Form ID) পড়ে নিয়ে RegEx দিয়ে ম্যাচ করে একটি নির্দিষ্ট রেজাল্ট রিটার্ন করে।
* **Trigger (শর্ত নির্ধারণ):** আপনি যদি চান শুধুমাত্র ব্লগ পেজের ফর্ম সাবমিশন ট্র্যাক করবেন, তবে ট্রিগারে RegEx লিখে দিলে ব্রাউজার অন্য পেজে থাকা অবস্থায় ওই ট্যাগটি ট্রিগার করবে না।

**সহজ কথায়:** GTM-এ RegEx হলো **"গেটকিপার"** বা পাহারাদার—যা ব্রাউজার থেকে ডাটা সার্ভারে যাওয়ার আগেই ফিল্টার বা ফরম্যাট করে দেয়।

---

### ২. BigQuery / SQL-এ RegEx যেভাবে কাজ করে

BigQuery-তে ডাটা আগেই জমা হয়ে থাকে (ডাটা ওয়্যারহাউস)। এখানে লাখ লাখ বা কোটি কোটি রো (Row) ডাটা থেকে নির্দিষ্ট প্যাটার্ন খুঁজে বের করার জন্য SQL-এর সাথে RegEx ফাংশন ব্যবহার করা হয়।

BigQuery-র প্রধান ৩টি ফাংশনের মূল কাজ:

* **`REGEXP_CONTAINS(text, pattern)`:**
* **কাজ:** এটি চেক করে লেখাতে প্যাটার্নটি আছে কি না। থাকলে `TRUE`, না থাকলে `FALSE` দেয়। (GTM-এর `test()` এর মতো)।
* **ব্যবহার:** নির্দিষ্ট পেজ বা ইভেন্ট ফিল্টার করতে `WHERE` ক্লজে ব্যবহৃত হয়।


* **`REGEXP_EXTRACT(text, pattern)`:**
* **কাজ:** এটি পুরো টেক্সট থেকে শুধু নির্দিষ্ট অংশটি কেটে আলাদা করে নিয়ে আসে।
* **ব্যবহার:** জটিল URL থেকে ক্যাটাগরি, প্রোডাক্ট আইডি বা UTM প্যারামিটার আলাদা করে নতুন কলাম তৈরি করতে।


* **`REGEXP_REPLACE(text, pattern, replacement)`:**
* **কাজ:** টেক্সটের ভেতরের কোনো অংশ খুঁজে নিয়ে নতুন কিছু দিয়ে বদলে দেয়।
* **ব্যবহার:** ইউজারের ফোন নম্বর, ইমেইল বা সেনসিটিভ তথ্য মাস্ক করা কিংবা টাইপো ঠিক করার জন্য।



**সহজ কথায়:** BigQuery-তে RegEx হলো **"ডাটা প্রসেসর"**—যা জমা থাকা বিশাল অগোছালো ডাটাকে এনালিটিক্স বা রিপোর্টিংয়ের উপযোগী করে সাজাতে সাহায্য করে।

---

### মূল পার্থক্য (কী খেয়াল রাখবেন)

* **ইনজিন:** GTM ব্যবহার করে জাভাস্ক্রিপ্টের Standard RegEx Engine, আর BigQuery ব্যবহার করে Google-এর **RE2 Engine**।
* **সিনট্যাক্স:** BigQuery-তে RegEx প্যাটার্নের আগে `r` লিখতে হয় (যেমন: `r'\d+'`), যাতে ব্যাকস্ল্যাশ (`\`) নিয়ে কোনো কনফিউশন না তৈরি হয়।

ডাটা অ্যানালিটিক্সে দক্ষ হতে এই দুটি জায়গায় RegEx-এর ব্যবহার বুঝতে পারা অত্যন্ত গুরুত্বপূর্ণ।




