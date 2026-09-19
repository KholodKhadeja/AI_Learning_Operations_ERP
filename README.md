# AI Learning Operations ERP

מערכת ERP חכמה לניהול ואוטומציה של תהליכי העבודה בחברת פיתוח למידה דיגיטלית.

## 🎯 מטרת הפרויקט

המערכת מנהלת את מחזור החיים העסקי והתפעולי של מוצר למידה דיגיטלי — החל מקבלת Lead, דרך מכירה, הצעת מחיר ותשלום, ועד לניהול הפרויקט, אישורי לקוח ופרסום המוצר.

המערכת משלבת **n8n, AI Agents, RAG, Airtable, Gmail, Google Calendar ו-Web App** שנבנה באמצעות Claude Code.

## 🔄 התהליך המרכזי

**Lead → Qualified Lead → Proposal → Customer → Payment → Project → Production → QA → Client Review → Approval → Publication**

כל פרויקט עובר באותו pipeline, ללא תלות בסוג מוצר הלמידה.

## 📚 סוגי מוצרים

- קורס אונליין
- קורס פרונטלי
- קורס היברידי
- לומדה
- סרטון הדרכה
- משחק למידה
- מצגת
- סימולציה
- Micro-credential

## 👥 משתמשים

- **Admin / CEO / VP** – תמונת מצב מלאה וניהול המערכת
- **Project Manager** – צפייה וניהול של הפרויקטים שהוקצו אליו
- **Client** – צפייה בפרויקט שלו, התקדמות ואישורים
- **Lead / Customer** – תקשורת מול החברה בתהליך המכירה והפרויקט

## 🤖 AI Agents

### Sales Agent
מטפל בתהליך המכירה מול Lead באמצעות Gmail:
- איסוף דרישות חסרות
- ניתוח תשובות
- עדכון Lead
- זיהוי Lead שמוכן לתמחור

### Project Manager Agent
מאפשר ל-PM לשאול שאלות על הפרויקטים שלו:
- מה סטטוס הפרויקט?
- באיזה שלב אנחנו?
- מה הושלם ומה השלב הבא?
- האם ממתינים ללקוח?

### Client Agent
משלב בין:
- **RAG** – ידע כללי ויציב על החברה, השירותים והמוצרים
- **Airtable** – מידע דינמי וספציפי לפרויקט

## 🧠 RAG

מאגר הידע משמש למידע כללי על החברה, למשל:
- קטלוג מוצרים
- שירותים
- תהליכי עבודה
- FAQ
- מידע על החברה
- הנחיות תקשורת

**RAG = ידע כללי ויציב**
**Airtable = מידע דינמי וספציפי לפרויקט**

## 🔗 Workflows

| שם ה־Workflow                                                                             | תיאור קצר                                                                                                       |
| ------------------------------------------------------------------------------------------ | ----------------------------------------------------------------------------------------------------------------- |
| [RAG Ingestion Workflow](https://kholod-khadeja.app.n8n.cloud/workflow/nOAu9zc5KiuWEFHn) | וורקפלו לקליטת קבצי ידע, עיבוד ויצירת Embeddings באמצעות AI, ושמירתם ב־Qdrant לצורך שימוש עתידי במערכת ה־RAG. |

## ⚙️ אוטומציות מרכזיות ב-n8n

1. יצירת Lead חדש
2. ניהול תהליך Sales Agent
3. עיבוד מיילים נכנסים
4. יצירת Proposal
5. אישור Proposal
6. עדכון Payment
7. יצירת Project אוטומטית לאחר אישור ותשלום
8. ניהול שלבי הפרויקט
9. Client Review ו-Client Approval
10. פעולות AI ו-RAG

## 🗂️ Data Layer

**Airtable** משמש כ-Source of Truth עבור:
- Users
- Leads
- Customers
- Products
- Proposals
- Payments
- Projects
- Project Stages
- Tasks
- Client Feedback
- Files

## 🔌 אינטגרציות

- **Gmail** – תקשורת עם Leads ולקוחות
- **Google Calendar** – חיבור ליומנים האישיים של המשתמשים באמצעות הרשאת Google OAuth
- **n8n** – orchestration, workflows, AI ו-RAG
- **Claude Code** – בניית ממשק ה-Web App
- **Airtable** – בסיס הנתונים המרכזי

## 🏗️ ארכיטקטורה בקצרה

```text
Users / Clients / Leads
          │
          ▼
     Web App / Gmail
          │
          ▼
        n8n
   ┌──────┼────────┐
   ▼      ▼        ▼
 AI Agents  RAG   Workflows
   │      │        │
   └──────┼────────┘
          ▼
       Airtable
          │
          ├── Projects
          ├── Leads
          ├── Customers
          └── Tasks / Feedback / Files

Google Calendar ◄── Google OAuth
Gmail ◄──────────── n8n
```

## 🔐 עקרונות הרשאה

המערכת מפרידה בין הרשאות המשתמשים:
- PM רואה את הפרויקטים שהוקצו אליו.
- Client רואה רק את הפרויקט/ים המורשים שלו.
- Admin / CEO / VP מקבלים תמונת מצב מלאה.
- פעולות רגישות מתבצעות דרך n8n/server-side ולא באמצעות חשיפת credentials בצד הלקוח.

## 🚀 מטרת הדמו

להדגים תהליך End-to-End:

**Lead נכנס → AI אוסף דרישות → Proposal → אישור → Payment → Project נוצר אוטומטית → PM מוקצה → הפרויקט מתקדם בשלבים → Client מקבל עדכון ואישור → תיקונים במידת הצורך → QA → אישור סופי → Publication**

---

> **AI Learning Operations ERP**
> From Lead to Published Learning Product — automated with AI & n8n.
