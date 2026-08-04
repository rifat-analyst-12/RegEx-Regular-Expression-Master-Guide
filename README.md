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

```python
import os
from weasyprint import HTML

html_content = """<!DOCTYPE html>
<html lang="bn">
<head>
    <meta charset="UTF-8">
    <title>RegEx (Regular Expression) - একদম শূন্য থেকে জিরো টু হিরো গাইড</title>
    <style>
        @page {
            size: A4;
            margin: 18mm 15mm 18mm 15mm;
            background-color: #fcfcfd;
            @bottom-right {
                content: "পৃষ্ঠা " counter(page) " / " counter(pages);
                font-family: 'Segoe UI', Tahoma, 'SolaimanLipi', sans-serif;
                font-size: 9pt;
                color: #718096;
            }
            @bottom-left {
                content: "RegEx Complete Master Guide";
                font-family: 'Segoe UI', Tahoma, 'SolaimanLipi', sans-serif;
                font-size: 9pt;
                color: #718096;
            }
        }

        *, *::before, *::after {
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, 'SolaimanLipi', sans-serif;
            color: #2d3748;
            line-height: 1.6;
            margin: 0;
            padding: 0;
            font-size: 10.5pt;
        }

        /* Header Banner */
        .header-banner {
            background: linear-gradient(135deg, #1e3c72 0%, #2a5298 100%);
            color: #ffffff;
            padding: 25px 20px;
            border-radius: 8px;
            margin: -18mm -15mm 25px -15mm;
            padding-left: 20mm;
            padding-right: 20mm;
            padding-top: 20mm;
        }

        .header-banner h1 {
            font-size: 22pt;
            margin: 0 0 8px 0;
            font-weight: 700;
            letter-spacing: -0.5px;
            color: #ffffff;
        }

        .header-banner p {
            font-size: 12pt;
            margin: 0;
            opacity: 0.9;
            font-weight: 300;
        }

        .intro-box {
            background-color: #ebf8ff;
            border-left: 4px solid #3182ce;
            padding: 15px;
            border-radius: 0 6px 6px 0;
            margin-bottom: 25px;
        }

        .intro-box h3 {
            margin-top: 0;
            color: #2b6cb0;
            font-size: 13pt;
        }

        h2 {
            color: #1a202c;
            font-size: 15pt;
            border-bottom: 2px solid #e2e8f0;
            padding-bottom: 6px;
            margin-top: 28px;
            margin-bottom: 14px;
            page-break-after: avoid;
        }

        h3 {
            color: #2d3748;
            font-size: 12.5pt;
            margin-top: 18px;
            margin-bottom: 8px;
            page-break-after: avoid;
        }

        p {
            margin-top: 0;
            margin-bottom: 10px;
        }

        /* Pattern Cards & Tables */
        table {
            width: 100%;
            border-collapse: collapse;
            margin-bottom: 18px;
            font-size: 10pt;
            page-break-inside: auto;
        }

        tr {
            page-break-inside: avoid;
        }

        th {
            background-color: #2b6cb0;
            color: white;
            text-align: left;
            padding: 9px 12px;
            font-weight: 600;
        }

        td {
            padding: 9px 12px;
            border-bottom: 1px solid #e2e8f0;
            vertical-align: top;
        }

        tr:nth-child(even) {
            background-color: #f7fafc;
        }

        code {
            font-family: 'Courier New', Courier, monospace;
            background-color: #edf2f7;
            color: #c53030;
            padding: 2px 6px;
            border-radius: 4px;
            font-size: 9.5pt;
            font-weight: bold;
        }

        .regex-badge {
            font-family: 'Courier New', Courier, monospace;
            background-color: #2d3748;
            color: #68d391;
            padding: 3px 8px;
            border-radius: 4px;
            font-size: 10pt;
            display: inline-block;
            font-weight: bold;
        }

        .example-box {
            background-color: #ffffff;
            border: 1px solid #e2e8f0;
            border-radius: 6px;
            padding: 14px;
            margin-bottom: 16px;
            box-shadow: 0 1px 3px rgba(0,0,0,0.05);
            page-break-inside: avoid;
        }

        .example-title {
            font-weight: bold;
            color: #2b6cb0;
            font-size: 11pt;
            margin-bottom: 6px;
        }

        .match-highlight {
            background-color: #c6f6d5;
            color: #22543d;
            padding: 1px 4px;
            border-radius: 3px;
            font-weight: bold;
        }

        .no-match {
            background-color: #fed7d7;
            color: #742a2a;
            padding: 1px 4px;
            border-radius: 3px;
            text-decoration: line-through;
        }

        ul, ol {
            margin-top: 0;
            margin-bottom: 12px;
            padding-left: 20px;
        }

        li {
            margin-bottom: 4px;
        }

        .tip-box {
            background-color: #fefcbf;
            border-left: 4px solid #d69e2e;
            padding: 12px;
            border-radius: 0 6px 6px 0;
            margin: 15px 0;
            font-size: 10pt;
        }

        .cheatsheet-grid {
            display: table;
            width: 100%;
            table-layout: fixed;
            margin-bottom: 15px;
        }

        .cheatsheet-col {
            display: table-cell;
            width: 50%;
            padding-right: 10px;
        }

        .cheatsheet-col:last-child {
            padding-right: 0;
            padding-left: 10px;
        }
    </style>
</head>
<body>

    <div class="header-banner">
        <h1>RegEx (Regular Expression) মাস্টার গাইড</h1>
        <p>একদম নতুনদের জন্য বাস্তব জীবনভিত্তিক সহজ ও সম্পূর্ণ নির্দেশিকা</p>
    </div>

    <div class="intro-box">
        <h3>RegEx আসলে কী এবং কেন শিখবেন?</h3>
        <p><strong>RegEx</strong> (Regular Expression) হলো টেক্সট প্রসেসিং এবং সার্চ করার একটি অত্যন্ত শক্তিশালী সাংকেতিক ভাষা। সাধারণ <code>Ctrl + F</code> দিয়ে আপনি শুধু নির্দিষ্ট একটি শব্দ খুঁজতে পারেন। কিন্তু RegEx-এর মাধ্যমে আপনি টেক্সটের <strong>প্যাটার্ন বা ধরণ</strong> ধরে অনুসন্ধান করতে পারবেন। যেমন: কোনো ডকুমেন্টের সব মোবাইল নম্বর, ইমেইল আইডি, বা নির্দিষ্ট ফরম্যাটের তারিখ এক নিমেষে খুঁজে বের করা বা বদলে ফেলা।</p>
    </div>

    <h2>১. বেসিক বিল্ডিং ব্লকস (মৌলিক প্রতীকসমূহ)</h2>
    <p>RegEx শেখার প্রথম ধাপ হলো এর মূল বর্ণমালা বা প্রতীকগুলো চিনে নেওয়া:</p>

    <table>
        <thead>
            <tr>
                <th style="width: 20%;">চিহ্ন (Symbol)</th>
                <th style="width: 30%;">অর্থ (Meaning)</th>
                <th style="width: 50%;">ব্যাখ্যা ও উদাহরণ</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td><code>\d</code></td>
                <td>Digit (সংখ্যা)</td>
                <td>যেকোনো একটি সংখ্যা (0 থেকে 9)। যেমন: <code>\d</code> খুঁজে পাবে <code>5</code>।</td>
            </tr>
            <tr>
                <td><code>\D</code></td>
                <td>Non-digit (সংখ্যা নয়)</td>
                <td>সংখ্যা ছাড়া যেকোনো বর্ণ বা চিহ্ন।</td>
            </tr>
            <tr>
                <td><code>\w</code></td>
                <td>Word character (শব্দের বর্ণ)</td>
                <td>যেকোনো বর্ণ (A-Z, a-z), সংখ্যা (0-9) এবং আন্ডারস্কোর (_)।</td>
            </tr>
            <tr>
                <td><code>\W</code></td>
                <td>Non-word character</td>
                <td>অক্ষর/সংখ্যা/আন্ডারস্কোর ছাড়া বাকি সব চিহ্ন (স্পেস, @, #, $, ইত্যাদি)।</td>
            </tr>
            <tr>
                <td><code>\s</code></td>
                <td>Whitespace (স্পেস)</td>
                <td>স্পেস (Space), ট্যাബ്‌ (Tab) বা নতুন লাইন (Newline)।</td>
            </tr>
            <tr>
                <td><code>.</code></td>
                <td>Any character (যেকোনো কিছু)</td>
                <td>নতুন লাইন ছাড়া যেকোনো একটি বর্ণ, সংখ্যা বা প্রতীক।</td>
            </tr>
        </tbody>
    </table>

    <h2>২. কোয়ান্টিফায়ার (পরিমাণ নির্ধারণকারী চিহ্ন)</h2>
    <p>কোনো চিহ্ন কতবার থাকবে, তা নির্ধারণ করতে নিচের কোয়ান্টিফায়ারগুলো ব্যবহার করা হয়:</p>

    <table>
        <thead>
            <tr>
                <th style="width: 20%;">কোয়ান্টিফায়ার</th>
                <th style="width: 30%;">অর্থ</th>
                <th style="width: 50%;">উদাহরণ</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td><code>+</code></td>
                <td>১ বা তার বেশি (At least 1)</td>
                <td><code>\d+</code> মানে হলো অন্তত ১টি বা পর পর একাধিক সংখ্যা (যেমন: 1234)।</td>
            </tr>
            <tr>
                <td><code>*</code></td>
                <td>০ বা তার বেশি (0 or more)</td>
                <td>উপস্থিত থাকতেও পারে, নাও থাকতে পারে বা অনেকবার থাকতে পারে।</td>
            </tr>
            <tr>
                <td><code>?</code></td>
                <td>০ বা ১ বার (Optional)</td>
                <td>ঐচ্ছিক উপাদান। যেমন: <code>colou?r</code> দিয়ে color এবং colour দুটিই মিলবে।</td>
            </tr>
            <tr>
                <td><code>{n}</code></td>
                <td>ঠিক n বার</td>
                <td><code>\d{4}</code> মানে ঠিক ৪টি সংখ্যা (যেমন: 2026)।</td>
            </tr>
            <tr>
                <td><code>{n,m}</code></td>
                <td>n থেকে m বার</td>
                <td><code>\d{2,4}</code> মানে ২টি থেকে ৪টি সংখ্যার জোট।</td>
            </tr>
        </tbody>
    </table>

    <h2>৩. বাস্তব জীবনের ৪টি দারুণ উদাহরণ</h2>

    <div class="example-box">
        <div class="example-title">উদাহরণ ১: বাংলাদেশের মোবাইল নম্বর শনাক্তকরণ</div>
        <p><strong>লক্ষ্য:</strong> একটি লেখায় থাকা বাংলাদেশি মোবাইল নম্বরগুলো (যেমন: 01712345678 বা 01800000000) খুঁজে বের করা।</p>
        <p><strong>RegEx প্যাটার্ন:</strong> <span class="regex-badge">01[3-9]\d{8}</span></p>
        <p><strong>প্যাটার্নের ব্যবচ্ছেদ:</strong></p>
        <ul>
            <li><code>01</code> - নম্বরটি অবশ্যই '01' দিয়ে শুরু হতে হবে।</li>
            <li><code>[3-9]</code> - ৩য় নম্বরটি ৩ থেকে ৯-এর মধ্যে হতে হবে (কারণ বাংলাদেশে 010, 011, 012 সাধারণত ব্যবহৃত হয় না)।</li>
            <li><code>\d{8}</code> - এরপর আরও ঠিক ৮টি সংখ্যা থাকবে। (মোট ১১ ডিজিট)।</li>
        </ul>
        <p><strong>ফলাফল:</strong></p>
        <ul>
            <li><span class="match-highlight">01712345678</span> (ম্যাচ করেছে)</li>
            <li><span class="match-highlight">01987654321</span> (ম্যাচ করেছে)</li>
            <li><span class="no-match">01234567890</span> (ম্যাচ করবে না - ৩য় ডিজিট '2')</li>
            <li><span class="no-match">01712345</span> (ম্যাচ করবে না - ডিজিট কম)</li>
        </ul>
    </div>

    <div class="example-box">
        <div class="example-title">উদাহরণ ২: ইমেইল ঠিকানা (Email Address) ফিল্টার করা</div>
        <p><strong>লক্ষ্য:</strong> যেকোনো বৈধ ইমেইল অ্যাড্রেস (যেমন: <code>rahim12@gmail.com</code>) বের করা।</p>
        <p><strong>RegEx প্যাটার্ন:</strong> <span class="regex-badge">[\w.-]+@[\w.-]+\.\w+</span></p>
        <p><strong>প্যাটার্নের ব্যবচ্ছেদ:</strong></p>
        <ul>
            <li><code>[\w.-]+</code> - @ চিহ্নের আগে এক বা একাধিক অক্ষর, সংখ্যা, ডট বা হাইফেন।</li>
            <li><code>@</code> - একটি অবশ্যই থাকা আবশ্যক '@' চিহ্ন।</li>
            <li><code>[\w.-]+</code> - ডোমেইন নাম (যেমন: gmail, yahoo)।</li>
            <li><code>\.</code> - একটি আসল ডট (.) চিহ্ন (যেহেতু ডট নিজে একটি স্পেশাল ক্যারেক্টার, তাই ব্যাকস্ল্যাশ দেওয়া হয়েছে)।</li>
            <li><code>\w+</code> - ডোমেইন এক্সটেনশন (যেমন: com, org, net)।</li>
        </ul>
        <p><strong>ফলাফল:</strong></p>
        <ul>
            <li><span class="match-highlight">karim.test_1@gmail.com</span> (ম্যাচ করেছে)</li>
            <li><span class="match-highlight">info@company.com.bd</span> (ম্যাচ করেছে)</li>
            <li><span class="no-match">invalid-email@</span> (ম্যাচ করবে না - ডোমেইন নেই)</li>
        </ul>
    </div>

    <div class="example-box">
        <div class="example-title">উদাহরণ ৩: তারিখ (Date Format) শনাক্ত করা</div>
        <p><strong>লক্ষ্য:</strong> DD-MM-YYYY বা DD/MM/YYYY ফরম্যাটের তারিখ খোঁজা (যেমন: 15-08-2026)।</p>
        <p><strong>RegEx প্যাটার্ন:</strong> <span class="regex-badge">\d{2}[-/]\d{2}[-/]\d{4}</span></p>
        <p><strong>প্যাটার্নের ব্যবচ্ছেদ:</strong></p>
        <ul>
            <li><code>\d{2}</code> - ২ ডিজিটের দিন (যেমন: 15)।</li>
            <li><code>[-/]</code> - একটি হাইফেন (-) অথবা একটি স্ল্যাশ (/) চিহ্ন।</li>
            <li><code>\d{2}</code> - ২ ডিজিটের মাস (যেমন: 08)।</li>
            <li><code>[-/]</code> - পুনারায় হাইফেন (-) অথবা স্ল্যাশ (/) চিহ্ন।</li>
            <li><code>\d{4}</code> - ৪ ডিজিটের বছর (যেমন: 2026)।</li>
        </ul>
        <p><strong>ফলাফল:</strong></p>
        <ul>
            <li><span class="match-highlight">15-08-2026</span> (ম্যাচ করেছে)</li>
            <li><span class="match-highlight">01/12/2025</span> (ম্যাচ করেছে)</li>
            <li><span class="no-match">2026-08-15</span> (ম্যাচ করবে না - ফরম্যাট ভিন্ন)</li>
        </ul>
    </div>

    <div class="example-box">
        <div class="example-title">উদাহরণ ৪: স্ট্রং পাসওয়ার্ড যাচাইকরণ (Validation)</div>
        <p><strong>লক্ষ্য:</strong> একটি পাসওয়ার্ডে অন্তত একটি ছোট হাতের অক্ষর, একটি বড় হাতের অক্ষর, একটি সংখ্যা এবং ন্যূনতম ৮টি অক্ষর আছে কি না চেক করা।</p>
        <p><strong>RegEx প্যাটার্ন:</strong> <span class="regex-badge">^(?=.*[a-z])(?=.*[A-Z])(?=.*\d).{8,}$</span></p>
        <p><strong>প্যাটার্নের ব্যবচ্ছেদ:</strong></p>
        <ul>
            <li><code>^</code> - লেখার শুরু এবং <code>$</code> - লেখার শেষ।</li>
            <li><code>(?=.*[a-z])</code> - অন্তত একটি ছোট হাতের অক্ষর (a-z) থাকতে হবে।</li>
            <li><code>(?=.*[A-Z])</code> - অন্তত একটি বড় হাতের অক্ষর (A-Z) থাকতে হবে।</li>
            <li><code>(?=.*\d)</code> - অন্তত একটি সংখ্যা (0-9) থাকতে হবে।</li>
            <li><code>.{8,}</code> - মোট দৈর্ঘ্য কমপক্ষে ৮টি ক্যারেক্টার হতে হবে।</li>
        </ul>
    </div>

    <h2>৪. পজিশনিং বা বাউন্ডারি চিহ্ন (Anchors)</h2>
    <p>লেখার কোন জায়গায় প্যাটার্নটি থাকবে তা নির্দিষ্ট করার চিহ্ন:</p>
    <ul>
        <li><code>^</code> (Caret): লাইনের <strong>শুরুতে</strong> ম্যাচ করায়। যেমন: <code>^Hello</code> (লাইনটি Hello দিয়ে শুরু হতে হবে)।</li>
        <li><code>$</code> (Dollar): লাইনের <strong>শেষে</strong> ম্যাচ করায়। যেমন: <code>end$</code> (লাইনটি end দিয়ে শেষ হতে হবে)।</li>
        <li><code>\b</code> (Word Boundary): কোনো নির্দিষ্ট <strong>শব্দের সীমানা</strong> তৈরি করে। যেমন: <code>\bcat\b</code> লিখলে শুধু স্বাধীন শব্দ "cat" মিলবে, "concatenate" বা "catfish"-এর ভেতরের "cat" মিলবে না।</li>
    </ul>

    <div class="tip-box">
        <strong>💡 কিভাবে প্র্যাকটিস করবেন?</strong><br>
        অনলাইনে প্র্যাকটিস করার জন্য সবচেয়ে সেরা ওয়েবসাইট হলো <strong><a href="https://regex101.com" style="color: #b7791f;">regex101.com</a></strong>। সেখানে গিয়ে 'Flavor' অপশনে Python, JavaScript বা PCRE সিলেক্ট করে উপরের উদাহরণগুলো নিজে নিজে টাইপ করে টেস্ট করুন!
    </div>

    <h2>৫. কুইক রেফারেন্স শিট (সংক্ষেপে মনে রাখার উপায়)</h2>
    
    <table>
        <thead>
            <tr>
                <th>কাজ</th>
                <th>RegEx সিনট্যাক্স</th>
                <th>উদাহরণ</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>যেকোনো সংখ্যা ধরা</td>
                <td><code>\d+</code></td>
                <td>123, 999, 0</td>
            </tr>
            <tr>
                <td>যেকোনো শব্দ ধরা</td>
                <td><code>\w+</code></td>
                <td>Hello, User_123</td>
            </tr>
            <tr>
                <td>ঐচ্ছিক অক্ষর (Optional)</td>
                <td><code>https?</code></td>
                <td>http, https</td>
            </tr>
            <tr>
                <td>নির্দিষ্ট ক্যারেক্টার সেট</td>
                <td><code>[aeiou]</code></td>
                <td>যেকোনো ভাওয়েল (Vowel) বর্ণ</td>
            </tr>
            <tr>
                <td>রেঞ্জ বা সীমা</td>
                <td><code>[A-Z]</code></td>
                <td>যেকোনো বড় হাতের অক্ষর</td>
            </tr>
            <tr>
                <td>গ্রুপিং (Group)</td>
                <td><code>(cat|dog)</code></td>
                <td>cat অথবা dog শব্দ</td>
            </tr>
        </tbody>
    </table>

</body>
</html>
"""

with open("regex_master_guide.html", "w", encoding="utf-8") as f:
    f.write(html_content)

HTML("regex_master_guide.html").write_pdf("RegEx_Master_Guide.pdf")
print("PDF Generated successfully!")


```

```text
PDF Generated successfully!


```

আপনার ভবিষ্যৎ ডকুমেন্টেশন এবং শেখার সুবিধার জন্য **RegEx (Regular Expression)**-এর উপর একটি পূর্ণাঙ্গ ও বিস্তারিত গাইড প্রস্তুত করা হয়েছে।

আপনার ব্যবহারের জন্য গাইডটি দিয়ে একটি সুন্দর ও প্রফেশনাল PDF ডকুমেন্ট তৈরি করা হয়েছে:


---

### 📖 RegEx (Regular Expression) সম্পূর্ণ গাইডলাইন

---

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

```python
html_content = """<!DOCTYPE html>
<html lang="bn">
<head>
    <meta charset="UTF-8">
    <title>RegEx Advanced & Practical Guide (রেগুলার এক্সপ্রেশন মাস্টারক্লাস - পার্ট ২)</title>
    <style>
        @page {
            size: A4;
            margin: 18mm 15mm 18mm 15mm;
            background-color: #fcfcfd;
            @bottom-right {
                content: "পৃষ্ঠা " counter(page) " / " counter(pages);
                font-family: 'Segoe UI', Tahoma, 'SolaimanLipi', sans-serif;
                font-size: 9pt;
                color: #718096;
            }
            @bottom-left {
                content: "RegEx Advanced Master Guide - Part 2";
                font-family: 'Segoe UI', Tahoma, 'SolaimanLipi', sans-serif;
                font-size: 9pt;
                color: #718096;
            }
        }

        *, *::before, *::after {
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, 'SolaimanLipi', sans-serif;
            color: #2d3748;
            line-height: 1.6;
            margin: 0;
            padding: 0;
            font-size: 10.5pt;
        }

        /* Header Banner */
        .header-banner {
            background: linear-gradient(135deg, #0f766e 0%, #115e59 100%);
            color: #ffffff;
            padding: 25px 20px;
            border-radius: 8px;
            margin: -18mm -15mm 25px -15mm;
            padding-left: 20mm;
            padding-right: 20mm;
            padding-top: 20mm;
        }

        .header-banner h1 {
            font-size: 22pt;
            margin: 0 0 8px 0;
            font-weight: 700;
            letter-spacing: -0.5px;
            color: #ffffff;
        }

        .header-banner p {
            font-size: 12pt;
            margin: 0;
            opacity: 0.9;
            font-weight: 300;
        }

        .intro-box {
            background-color: #f0fdf4;
            border-left: 4px solid #16a34a;
            padding: 15px;
            border-radius: 0 6px 6px 0;
            margin-bottom: 25px;
        }

        .intro-box h3 {
            margin-top: 0;
            color: #15803d;
            font-size: 13pt;
        }

        h2 {
            color: #1a202c;
            font-size: 15pt;
            border-bottom: 2px solid #e2e8f0;
            padding-bottom: 6px;
            margin-top: 28px;
            margin-bottom: 14px;
            page-break-after: avoid;
        }

        h3 {
            color: #2d3748;
            font-size: 12.5pt;
            margin-top: 18px;
            margin-bottom: 8px;
            page-break-after: avoid;
        }

        p {
            margin-top: 0;
            margin-bottom: 10px;
        }

        table {
            width: 100%;
            border-collapse: collapse;
            margin-bottom: 18px;
            font-size: 10pt;
            page-break-inside: auto;
        }

        tr {
            page-break-inside: avoid;
        }

        th {
            background-color: #0f766e;
            color: white;
            text-align: left;
            padding: 9px 12px;
            font-weight: 600;
        }

        td {
            padding: 9px 12px;
            border-bottom: 1px solid #e2e8f0;
            vertical-align: top;
        }

        tr:nth-child(even) {
            background-color: #f7fafc;
        }

        code {
            font-family: 'Courier New', Courier, monospace;
            background-color: #edf2f7;
            color: #c53030;
            padding: 2px 6px;
            border-radius: 4px;
            font-size: 9.5pt;
            font-weight: bold;
        }

        .regex-badge {
            font-family: 'Courier New', Courier, monospace;
            background-color: #1e293b;
            color: #4ade80;
            padding: 3px 8px;
            border-radius: 4px;
            font-size: 10pt;
            display: inline-block;
            font-weight: bold;
        }

        .example-box {
            background-color: #ffffff;
            border: 1px solid #e2e8f0;
            border-radius: 6px;
            padding: 14px;
            margin-bottom: 16px;
            box-shadow: 0 1px 3px rgba(0,0,0,0.05);
            page-break-inside: avoid;
        }

        .example-title {
            font-weight: bold;
            color: #0f766e;
            font-size: 11pt;
            margin-bottom: 6px;
        }

        .match-highlight {
            background-color: #dcfce7;
            color: #166534;
            padding: 1px 4px;
            border-radius: 3px;
            font-weight: bold;
        }

        .no-match {
            background-color: #fee2e2;
            color: #991b1b;
            padding: 1px 4px;
            border-radius: 3px;
            text-decoration: line-through;
        }

        ul, ol {
            margin-top: 0;
            margin-bottom: 12px;
            padding-left: 20px;
        }

        li {
            margin-bottom: 4px;
        }

        .code-block {
            background-color: #1e293b;
            color: #f8fafc;
            padding: 12px;
            border-radius: 6px;
            font-family: 'Courier New', Courier, monospace;
            font-size: 9.5pt;
            margin-bottom: 12px;
            white-space: pre-wrap;
        }
    </style>
</head>
<body>

    <div class="header-banner">
        <h1>RegEx এডভান্সড মাস্টার গাইড (পার্ট ২)</h1>
        <p>বাস্তব প্রজেক্ট, কমপ্লেক্স প্যাটার্ন ও ডাটা ক্লিনআপ গাইড</p>
    </div>

    <div class="intro-box">
        <h3>এই পর্বে আপনি কী কী শিখবেন?</h3>
        <p>প্রথম পর্বে আপনি RegEx-এর মৌলিক উপাদান ও কোয়ান্টিফায়ার শিখেছেন। এই পার্ট ২-এ আমরা জানব <strong>গ্রুপিং (Grouping)</strong>, <strong>লুক-অ্যাহেড (Lookahead)</strong>, <strong>ডাটা রিপ্লেসমেন্ট (Search & Replace)</strong> এবং বাস্তব প্রজেক্টে ব্যবহৃত জটিল কিছু প্যাটার্ন!</p>
    </div>

    <h2>১. এডভান্সড কনসেপ্ট (গ্রুপিং ও ব্যাকরেফারেন্স)</h2>

    <table>
        <thead>
            <tr>
                <th style="width: 25%;">কনসেপ্ট / চিহ্ন</th>
                <th style="width: 35%;">কাজ</th>
                <th style="width: 40%;">উদাহরণ</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td><code>( ... )</code> (Capturing Group)</td>
                <td>নির্দিষ্ট অংশকে ব্র্যাকেটে ঘিরে গ্রুপ করা এবং মেমোরিতে ধরে রাখা।</td>
                <td><code>(\d{3})-(\d{4})</code> (কোড ও নম্বর আলাদা করা)</td>
            </tr>
            <tr>
                <td><code>(?: ... )</code> (Non-capturing Group)</td>
                <td>গ্রুপ করবে কিন্তু মেমোরিতে সেভ করবে না (পারফরম্যান্স ফাস্ট করার জন্য)।</td>
                <td><code>(?:http|https)://</code></td>
            </tr>
            <tr>
                <td><code>\1, \2</code> (Backreference)</td>
                <td>আগে গ্রুপে পাওয়া টেক্সটকে পুনরায় মেলানো।</td>
                <td><code>(\w+)\s+\1</code> (ডাবল হয়ে যাওয়া শব্দ যেমন "the the" ধরা)</td>
            </tr>
            <tr>
                <td><code>(?=...)</code> (Positive Lookahead)</td>
                <td>সামনে নির্দিষ্ট কিছু থাকলে তবেই ম্যাচ করবে (কিন্তু সেটিকে সিলেক্ট করবে না)।</td>
                <td><code>\d+(?=\$ )</code> (ডলার চিহ্নের আগে থাকা সংখ্যা ধরা)</td>
            </tr>
        </tbody>
    </table>

    <h2>২. বাস্তব জীবনের আরও ৫টি বাস্তব উদাহরণ</h2>

    <div class="example-box">
        <div class="example-title">উদাহরণ ৫: URL / ওয়েবসাইট লিঙ্ক এক্সট্র্যাক্ট করা</div>
        <p><strong>লক্ষ্য:</strong> যেকোনো HTTP বা HTTPS ওয়েবসাইট লিঙ্ক টেক্সট থেকে খুঁজে বের করা।</p>
        <p><strong>RegEx প্যাটার্ন:</strong> <span class="regex-badge">https?://[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}(?:/\S*)?</span></p>
        <p><strong>প্যাটার্নের ব্যাখ্যা:</strong></p>
        <ul>
            <li><code>https?://</code> - <code>http://</code> অথবা <code>https://</code> মেলানো (এখানে 's' ঐচ্ছিক)।</li>
            <li><code>[a-zA-Z0-9.-]+</code> - ডোমেইন নেম (যেমন: github বা google)।</li>
            <li><code>\.[a-zA-Z]{2,}</code> - ডট এবং অন্তত ২ অক্ষরের টিএলডি (যেমন: .com, .org, .edu)।</li>
            <li><code>(?:/\S*)?</code> - ইউআরএল-এর পেছনের পাথ (যদি থাকে)।</li>
        </ul>
    </div>

    <div class="example-box">
        <div class="example-title">উদাহরণ ৬: IP Address (IPv4) শনাক্ত করা</div>
        <p><strong>লক্ষ্য:</strong> নেটওয়ার্কের IP Address (যেমন: 192.168.1.1) ফিল্টার করা।</p>
        <p><strong>RegEx প্যাটার্ন:</strong> <span class="regex-badge">\b(?:\d{1,3}\.){3}\d{1,3}\b</span></p>
        <p><strong>প্যাটার্নের ব্যাখ্যা:</strong></p>
        <ul>
            <li><code>\d{1,3}\.</code> - ১ থেকে ৩ ডিজিটের সংখ্যা এবং একটি ডট (যেমন: 192.)।</li>
            <li><code>{3}</code> - এই ডট সহ সংখ্যার অংশটি পর পর ৩ বার রিপিট হবে (192.168.1.)।</li>
            <li><code>\d{1,3}</code> - শেষে শুধু ১ থেকে ৩ ডিজিটের একটি সংখ্যা থাকবে (1)।</li>
        </ul>
    </div>

    <div class="example-box">
        <div class="example-title">উদাহরণ ৭: HTML Tag এক্সট্র্যাকশন</div>
        <p><strong>লক্ষ্য:</strong> HTML কোডের ভেতরে থাকা ট্যাগগুলো ধরে ফেলা বা মুছে ফেলা (যেমন: <code>&lt;h1&gt;Header&lt;/h1&gt;</code>)।</p>
        <p><strong>RegEx প্যাটার্ন:</strong> <span class="regex-badge">&lt;[^&gt;]+&gt;</span></p>
        <p><strong>প্যাটার্নের ব্যাখ্যা:</strong></p>
        <ul>
            <li><code>&lt;</code> - শুরু হবে <code>&lt;</code> চিহ্ন দিয়ে।</li>
            <li><code>[^&gt;]+</code> - <code>&gt;</code> চিহ্ন না পাওয়া পর্যন্ত যেকোনো ক্যারেক্টার এক বা একাধিকবার থাকবে।</li>
            <li><code>&gt;</code> - শেষ হবে <code>&gt;</code> চিহ্ন দিয়ে।</li>
        </ul>
    </div>

    <div class="example-box">
        <div class="example-title">উদাহরণ ৮: সোশ্যাল মিডিয়া হ্যাশট্যাগ (#Hashtag) এবং মেশন (@Mention)</div>
        <p><strong>লক্ষ্য:</strong> পোস্টের ভেতর থেকে #bangladesh বা @username ফিল্টার করা।</p>
        <p><strong>RegEx প্যাটার্ন (Hashtag):</strong> <span class="regex-badge">#\w+</span></p>
        <p><strong>RegEx প্যাটার্ন (Mention):</strong> <span class="regex-badge">@\w+</span></p>
    </div>

    <div class="example-box">
        <div class="example-title">উদাহরণ ৯: ডুপ্লিকেট শব্দ (Repeated Words) ধরা</div>
        <p><strong>লক্ষ্য:</strong> ভুলবশত পর পর দুবার লেখা একই শব্দ (যেমন: "This is **is** a test") খুঁজে বের করা।</p>
        <p><strong>RegEx প্যাটার্ন:</strong> <span class="regex-badge">\b(\w+)\s+\1\b</span></p>
        <p><strong>প্যাটার্নের ব্যাখ্যা:</strong></p>
        <ul>
            <li><code>(\w+)</code> - প্রথম শব্দটি ১ নম্বর গ্রুপে ধরে মেমোরিতে রাখা হলো।</li>
            <li><code>\s+</code> - মাঝে এক বা একাধিক স্পেস।</li>
            <li><code>\1</code> - ঠিক প্রথম গ্রুপে পাওয়া শব্দটিই আবার রিপিট হলে ম্যাচ করবে।</li>
        </ul>
    </div>

    <h2>৩. টেক্সট রিপ্লেসমেন্ট (Search & Replace Magic)</h2>
    <p>VS Code বা যেকোনো টেক্সট এডিটর বা প্রোগ্রামিং ল্যাঙ্গুয়েজে RegEx দিয়ে শুধু সার্চ নয়, লেখার ফরম্যাট রূপান্তরও করা যায়:</p>

    <div class="code-block">
[ সার্চ টেক্সট ]  : 01712-345678 (ফোন নম্বর)
[ RegEx সার্চ ]   : (\d{5})-(\d{6})
[ Replace Pattern]: +880 $1 $2
[ আউটপুট টেক্সট ] : +880 01712 345678
    </div>

    <h2>৪. প্রোগ্রামিং ল্যাঙ্গুয়েজে RegEx ব্যবহারের কোড</h2>

    <h3>Python উদাহরণ:</h3>
    <div class="code-block">
import re

text = "যোগাযোগ করুন: info@example.com অথবা 01700000000"
emails = re.findall(r'[\w.-]+@[\w.-]+\.\w+', text)
phones = re.findall(r'01[3-9]\d{8}', text)

print("ইমেইল:", emails) # ['info@example.com']
print("ফোন:", phones)   # ['01700000000']
    </div>

    <h3>JavaScript উদাহরণ:</h3>
    <div class="code-block">
const text = "অর্ডার আইডি: #ORD-99823";
const pattern = /#ORD-\d+/g;
const match = text.match(pattern);

console.log(match); // ["#ORD-99823"]
    </div>

</body>
</html>
"""

with open("regex_master_guide_part2.html", "w", encoding="utf-8") as f:
    f.write(html_content)

from weasyprint import HTML
HTML("regex_master_guide_part2.html").write_pdf("RegEx_Master_Guide_Part2.pdf")
print("PDF Part 2 Generated successfully!")


```

```text
PDF Part 2 Generated successfully!


```

আপনার RegEx শেখার সুবিধার্থে এবং প্রজেক্টের কাজে লাগানোর জন্য আরও **এডভান্সড কনসেপ্ট**, **জটিল বাস্তব উদাহরণ** এবং **প্রোগ্রামিংয়ে এর ব্যবহার** নিয়ে পার্ট ২ তৈরি করে দেওয়া হলো।

আপনার ডাউনলোডের জন্য একটি দ্বিতীয় PDF ফাইলও তৈরি করা হয়েছে:


---

### 📖 RegEx এডভান্সড মাস্টার গাইড (পার্ট ২)

---

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
