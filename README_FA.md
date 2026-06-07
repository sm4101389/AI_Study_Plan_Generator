# 📚 تولید‌کننده هوشمند برنامه مطالعه

یک خط‌لوله قدرتمند مبتنی بر مدل زبانی بزرگ (LLM) که هر گونه محتوای درسی را به یک برنامه مطالعه شخصی‌سازی‌شده تبدیل می‌کند. این ابزار محتوا را تحلیل می‌کند، مفاهیم را استخراج می‌نماید، وابستگی‌ها را مشخص می‌سازد، نیازهای دانشجو را ارزیابی می‌کند، زمان مطالعه را تخصیص می‌دهد و سوالات آزمونی تولید می‌کند – همه در یک گردش کاری خودکار.

![Python](https://img.shields.io/badge/Python-3.9+-blue.svg)
![LangChain](https://img.shields.io/badge/LangChain-1.3+-green.svg)
![OpenAI](https://img.shields.io/badge/OpenAI-Compatible-orange.svg)

## ✨ ویژگی‌ها

- **تحلیل درس** – استخراج موضوعات اصلی، سطح دشواری و بخش‌های مهم امتحان
- **استخراج مفاهیم** – شناسایی مفاهیم کلیدی همراه با درجه اهمیت و توضیح مختصر
- **نقشه وابستگی** – تعیین ترتیب یادگیری و پیش‌نیازها
- **ارزیابی دانشجو** – تشخیص نقاط قوت، ضعف و مباحث پرخطر برای یک دانشجوی معمولی
- **تخصیص زمان** – توزیع هوشمندانه ساعات مطالعه موجود بین مباحث
- **انتخاب راهکارها** – پیشنهاد روش‌هایی مانند یادگیری فعال، تکرار فاصله‌دار، آزمون شبیه‌سازی شده
- **بر

This is a well-structured Jupyter notebook that implements an AI-powered personalized study plan generator using LangChain and OpenAI. Here's a summary of what it does and some observations:
What the Code Does

This notebook creates a 9-step pipeline that:

    Analyzes course material - extracts main topics, difficulty levels, and exam-critical sections

    Extracts concepts - identifies major concepts with importance levels

    Maps dependencies - determines learning order and prerequisites

    Assesses student - identifies strengths, weaknesses, and high-risk topics

    Allocates time - distributes study hours based on concept importance and assessment

    Selects strategies - recommends learning methods (flashcards, active recall, etc.)

    Generates study plan - creates a detailed day-by-day schedule

    Generates quizzes - creates 10 exam-style questions (MCQs, short answers)

    Creates final report - compiles everything into a personalized learning plan

llm = ChatOpenAI(
    model="gpt-3.5-turbo",  # or "gpt-4", "gpt-4-turbo"
    temperature=0.3,
    openai_api_key="sk-............",
    openai_api_base="https://api.gapgpt.app/v1"
)

2. Empty API Key

You need to provide a valid API key:
python

# 📚 AI Study Plan Generator

An intelligent, LLM-powered pipeline that transforms any course material into a personalized study plan. It analyzes content, extracts concepts, maps dependencies, assesses student needs, allocates study time, and generates quizzes—all in one automated workflow.

![Python](https://img.shields.io/badge/Python-3.9+-blue.svg)
![LangChain](https://img.shields.io/badge/LangChain-1.3+-green.svg)
![OpenAI](https://img.shields.io/badge/OpenAI-Compatible-orange.svg)

## ✨ Features

- **Course analysis** – Extracts main topics, difficulty levels, and exam-critical sections
- **Concept extraction** – Identifies key concepts with importance ratings and explanations
- **Dependency mapping** – Builds prerequisite chains and optimal learning order
- **Student assessment** – Detects typical strengths, weaknesses, and high‑risk topics
- **Time allocation** – Distributes total available study hours intelligently
- **Strategy selection** – Recommends active recall, spaced repetition, mock exams, etc.
- **Daily study plan** – Generates a day‑by‑day schedule including revision sessions
- **Quiz generation** – Creates 10 exam‑style questions (MCQs, short answers)
- **Final report** – Combines all outputs into one personalized learning guide

## 🧠 How It Works

The pipeline runs nine sequential LLM calls, each building on the previous output:

Course Material
↓

    Course Analysis
    ↓

    Concept Extraction
    ↓

    Dependency Mapping
    ↓

    Student Assessment
    ↓

    Time Allocation
    ↓

    Strategy Selection
    ↓

    Study Plan Generation
    ↓

    Quiz Generation
    ↓

    Final Report

text


All steps are orchestrated without an external graph library – just plain Python functions and a shared state dictionary.

## 🔧 Prerequisites

- Python 3.9 or higher
- An OpenAI‑compatible API endpoint (or official OpenAI API)
- API key with access to a chat model (e.g., GPT‑3.5‑Turbo, GPT‑4)

## 📦 Installation

Clone the repository and install the required packages:

```bash
git clone https://github.com/yourusername/ai-study-plan-generator.git
cd ai-study-plan-generator
pip install langchain langchain-openai openai

    Note: The notebook uses a custom Aliyun mirror. For standard installation, simply run the command above.

⚙️ Configuration

Open the Jupyter notebook and locate the ChatOpenAI initialization cell. Replace the placeholders with your actual credentials:
python

llm = ChatOpenAI(
    model="gpt-3.5-turbo",          # or "gpt-4", "gpt-4-turbo"
    temperature=0.3,
    openai_api_key="sk-...",        # your API key
    openai_api_base="https://api.openai.com/v1"  # or your custom endpoint
)

    If you are using a reverse proxy or a local LLM server (e.g., Ollama, LocalAI), point openai_api_base to that URL and adjust the model name accordingly.

🚀 Usage

    Start Jupyter Notebook:
    bash

    jupyter notebook

    Open the provided notebook (e.g., study_plan_generator.ipynb).

    Run all cells.

    When prompted, paste your course material (plain text, lecture notes, syllabus, etc.).

    The pipeline will execute (may take 30–60 seconds depending on content length and API speed).

    A complete Personalized Learning Plan will be printed at the end.

Optional Parameters

Inside the __main__ block you can adjust:
python

state: StudyState = {
    "course_material": material,
    "exam_days": 30,      # change to your actual exam days
    "daily_hours": 2,     # how many hours you can study per day
    ...
}

📝 Example Output (excerpt)
text

================================================================================
PERSONALIZED LEARNING PLAN
================================================================================

## COURSE ANALYSIS
Main topics: Linear Algebra, Calculus, Probability...
Difficulty: High for eigenvectors, medium for limits...

## STUDY PLAN (Days 1–30)
Day 1-3: Matrix operations (2h/day)
Day 4-5: Eigenvalues and eigenvectors...
...

## QUIZZES (Sample)
1. What is the determinant of a singular matrix? (Easy)
2. Prove that the eigenvectors of a symmetric matrix are orthogonal. (Hard)
...

🛠️ Customization

    Change the LLM – Swap ChatOpenAI for any LangChain‑compatible model (Anthropic, Cohere, etc.)

    Add more pipeline steps – Insert new nodes between existing ones (e.g., a “summary” step)

    Parallelize independent steps – Use asyncio or LangGraph to run concept extraction and assessment concurrently

    Persist state – Save intermediate results to JSON to resume after failures

is project is licensed under the MIT License – feel free to use and modify it for your own learning or commercial projects.
🤝 Contributing

Issues and pull requests are welcome! If you find a bug or have an idea for improvement, please open an issue first.
translate to persian

We need to translate the given English text to Persian. The user provided a mix: first a summary of the code (as if from an assistant), then the README content. They want translation to Persian. The final instruction: "translate to persian". So I will translate the entire content from "This is a well-structured Jupyter notebook..." through the end of the README (including license and contributing). I will produce a Persian version.

در ادامه ترجمه فارسی متن ارائه شده (شامل خلاصه اولیه و سپس محتوای README) آورده شده است:
خلاصه آنچه کد انجام می‌دهد

این نوت‌بوک Jupyter یک تولیدکننده برنامه مطالعه شخصی‌سازی‌شده مبتنی بر هوش مصنوعی است که با استفاده از LangChain و OpenAI پیاده‌سازی شده. در اینجا خلاصه‌ای از عملکرد و چند نکته مشاهده می‌شود:

این نوت‌بوک یک خط‌لوله ۹ مرحله‌ای ایجاد می‌کند که:

    مطالب درسی را تحلیل می‌کند – موضوعات اصلی، سطح دشواری و بخش‌های مهم امتحان را استخراج می‌نماید.

    مفاهیم را استخراج می‌کند – مفاهیم اصلی را همراه با درجه اهمیت شناسایی می‌کند.

    وابستگی‌ها را نقشه می‌کند – ترتیب یادگیری و پیش‌نیازها را تعیین می‌کند.

    دانشجو را ارزیابی می‌کند – نقاط قوت، ضعف و مباحث پرخطر را شناسایی می‌کند.

    زمان را تخصیص می‌دهد – ساعات مطالعه را بر اساس اهمیت مفاهیم و ارزیابی توزیع می‌کند.

    راهکارها را انتخاب می‌کند – روش‌های یادگیری (فلش‌کارت، یادگیری فعال و ...) را توصیه می‌کند.

    برنامه مطالعه را تولید می‌کند – یک برنامه روزانه دقیق ایجاد می‌کند.

    آزمک (Quiz) تولید می‌کند – ۱۰ سؤال به سبک امتحانی (چند گزینه‌ای، پاسخ کوتاه) می‌سازد.

    گزارش نهایی را ایجاد می‌کند – همه موارد را در یک برنامه یادگیری شخصی‌سازی‌شده گردآوری می‌کند.

python

llm = ChatOpenAI(
    model="gpt-3.5-turbo",  # یا "gpt-4", "gpt-4-turbo"
    temperature=0.3,
    openai_api_key="sk-............",
    openai_api_base="https://api.gapgpt.app/v1"
)

نکته: باید یک کلید API معتبر ارائه دهید.
📚 تولیدکننده برنامه مطالعه هوشمند (AI Study Plan Generator)

یک خط‌لوله قدرتمند مبتنی بر LLM که هر گونه محتوای درسی را به یک برنامه مطالعه شخصی‌سازی‌شده تبدیل می‌کند. این ابزار محتوا را تحلیل می‌کند، مفاهیم را استخراج می‌نماید، وابستگی‌ها را نقشه می‌زند، نیازهای دانشجو را ارزیابی می‌کند، زمان مطالعه را تخصیص می‌دهد و آزمک تولید می‌کند – همه در یک گردش کاری خودکار.

https://img.shields.io/badge/Python-3.9+-blue.svg
https://img.shields.io/badge/LangChain-1.3+-green.svg
https://img.shields.io/badge/OpenAI-Compatible-orange.svg
✨ ویژگی‌ها

    تحلیل درس – استخراج موضوعات اصلی، سطح دشواری و بخش‌های مهم امتحان

    استخراج مفاهیم – شناسایی مفاهیم کلیدی همراه با درجه اهمیت و توضیحات

    نقشه وابستگی – ساخت زنجیره پیش‌نیازها و ترتیب بهینه یادگیری

    ارزیابی دانشجو – تشخیص نقاط قوت، ضعف و مباحث پرخطر برای یک دانشجوی معمولی

    تخصیص زمان – توزیع هوشمندانه کل ساعات مطالعه در دسترس

    انتخاب راهکار – توصیه روش‌هایی مانند یادگیری فعال، تکرار فاصله‌دار، آزمون‌های شبیه‌سازی شده

    برنامه مطالعه روزانه – تولید برنامه روزبه‌روز شامل جلسات مرور

    تولید آزمک – ایجاد ۱۰ سؤال به سبک امتحانی (چند گزینه‌ای، پاسخ کوتاه)

    گزارش نهایی – ترکیب همه خروجی‌ها در یک راهنمای یادگیری شخصی

🧠 نحوه کار

خط‌لوله به صورت ترتیبی ۹ بار LLM را فراخوانی می‌کند و هر بار بر اساس خروجی مرحله قبل عمل می‌نماید:
text

مطالب درسی
      ↓
1. تحلیل درس
      ↓
2. استخراج مفاهیم
      ↓
3. نقشه وابستگی
      ↓
4. ارزیابی دانشجو
      ↓
5. تخصیص زمان
      ↓
6. انتخاب راهکار
      ↓
7. تولید برنامه مطالعه
      ↓
8. تولید آزمک
      ↓
9. گزارش نهایی

همه مراحل بدون استفاده از کتابخانه گراف خارجی – فقط با توابع ساده پایتون و یک دیکشنری حالت مشترک – هماهنگ شده‌اند.
🔧 پیش‌نیازها

    پایتون ۳.۹ یا بالاتر

    یک نقطه پایانی API سازگار با OpenAI (یا API رسمی OpenAI)

    کلید API با دسترسی به یک مدل چت (مانند GPT‑۳.۵‑Turbo، GPT‑۴)

📦 نصب

کلون کردن مخزن و نصب پکیج‌های مورد نیاز:
bash

git clone https://github.com/yourusername/ai-study-plan-generator.git
cd ai-study-plan-generator
pip install langchain langchain-openai openai

    نکته: نوت‌بوک از آینه سفارشی Aliyun استفاده می‌کند. برای نصب استاندارد، کافی است دستور بالا را اجرا کنید.

⚙️ پیکربندی

نوت‌بوک Jupyter را باز کنید و سلول مقداردهی اولیه ChatOpenAI را پیدا کنید. جایگزین‌ها را با اطلاعات واقعی خود عوض کنید:
python

llm = ChatOpenAI(
    model="gpt-3.5-turbo",          # یا "gpt-4", "gpt-4-turbo"
    temperature=0.3,
    openai_api_key="sk-...",        # کلید API شما
    openai_api_base="https://api.openai.com/v1"  # یا نقطه پایانی سفارشی شما
)

    اگر از پروکسی معکوس یا سرور LLM محلی (مانند Ollama، LocalAI) استفاده می‌کنید، openai_api_base را به آن آدرس تغییر دهید و نام مدل را متناسب تنظیم کنید.

🚀 طریقه استفاده

    Jupyter Notebook را اجرا کنید:
    bash

    jupyter notebook

    نوت‌بوک ارائه شده (مثلاً study_plan_generator.ipynb) را باز کنید.

    همه سلول‌ها را اجرا کنید.

    هنگامی که برنامه درخواست کرد، مطالب درسی خود (متن ساده، جزوه، سر فصل‌ها) را وارد کنید.

    خط‌لوله اجرا می‌شود (بسته به طول محتوا و سرعت API ممکن است ۳۰ تا ۶۰ ثانیه طول بکشد).

    در پایان یک برنامه یادگیری شخصی‌سازی‌شده کامل چاپ می‌شود.

پارامترهای اختیاری

درون بلوک __main__ می‌توانید مقادیر زیر را تغییر دهید:
python

state: StudyState = {
    "course_material": material,
    "exam_days": 30,      # تعداد روزهای تا امتحان را تغییر دهید
    "daily_hours": 2,     # ساعات مطالعه روزانه
    ...
}

📝 نمونه خروجی (بخش کوچکی)
text

================================================================================
برنامه یادگیری شخصی‌سازی‌شده
================================================================================

## تحلیل درس
موضوعات اصلی: جبر خطی، حساب دیفرانسیل و انتگرال، احتمالات...
سطح دشواری: برای مقادیر ویژه بالا، برای حدها متوسط...

## برنامه مطالعه (روزهای ۱ تا ۳۰)
روز ۱-۳: عملیات ماتریسی (۲ ساعت در روز)
روز ۴-۵: مقادیر ویژه و بردارهای ویژه...
...

## آزمک (نمونه)
۱. دترمینان یک ماتریس تکین چیست؟ (آسان)
۲. ثابت کنید بردارهای ویژه یک ماتریس متقارن متعامد هستند. (سخت)
...

🛠️ سفارشی‌سازی

    تغییر LLM – ChatOpenAI را با هر مدل سازگار با LangChain (Anthropic، Cohere و غیره) عوض کنید.

    افزودن مراحل بیشتر – گره‌های جدیدی بین مراحل موجود اضافه کنید (مثلاً یک مرحله «خلاصه‌سازی»).

    موازی‌سازی مراحل مستقل – از asyncio یا LangGraph برای اجرای همزمان استخراج مفاهیم و ارزیابی استفاده کنید.

    ذخیره حالت – نتایج میانی را در فایل JSON ذخیره کنید تا در صورت بروز خطا بتوانید از همان نقطه ادامه دهید.

⚠️ محدودیت‌های شناخته شده

    خط‌لوله به صورت ترتیبی ۹ بار LLM را فراخوانی می‌کند – هر بار تأخیر و هزینه توکن را افزایش می‌دهد.

    ارزیابی دانشجو یک «دانشجوی معمولی» را فرض می‌کند – هیچ ورودی واقعی از کاربر گرفته نمی‌شود (البته به راحتی قابل گسترش است).

    مدیریت خطا برای خرابی API وجود ندارد – بهتر است بلوک‌های try/except اضافه کنید.

📄 مجوز

این پروژه تحت مجوز MIT منتشر شده است – می‌توانید آزادانه از آن برای یادگیری شخصی یا پروژه‌های تجاری خود استفاده و تغییر دهید.
🤝 مشارکت

گزارش مشکلات (issue) و درخواست کشیدن (pull request) پذیرفته می‌شود. اگر باگی پیدا کردید یا ایده‌ای برای بهبود دارید، لطفاً ابتدا یک issue باز کنید.

موفق و پیروز باشید! 🎓

امیدوارم این ترجمه مفید باشد. اگر بخش خاصی نیاز به ویرایش دارد، خوشحال می‌شوم کمک کنم.
