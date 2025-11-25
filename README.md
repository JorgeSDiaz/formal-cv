# Formal CV

A professional, ATS-friendly CV template built with Astro, designed to fit perfectly on a single letter-sized page (8.5" x 11") with a clean two-column layout.

## 🌟 Features

- **Dual Language Support**: Create separate CVs in different languages (e.g., `cv-en.json` for English, `cv-es.json` for Spanish)
- **Two-Column Layout**: Optimized design with left column for Profile and Experience, right column for Skills, Education, Competencies, and Volunteering
- **Single Page Design**: Carefully crafted to fit all content on one page for optimal printing and ATS compatibility
- **Configurable Path**: Easy switching between different CV files using TypeScript path aliases
- **Print-Ready**: Optimized spacing and typography for professional printing

## 🚀 Getting Started

### 1. Create Your CV Data File

Copy `cv-example.json` and rename it to your desired filename (e.g., `cv-en.json` for English or `cv-es.json` for Spanish):

```bash
cp cv-example.json cv-en.json
```

### 2. Fill in Your Information

Edit your new CV file with your personal information. See the **CV Structure Guide** below for detailed field explanations.

### 3. Configure the Path Alias

Edit `tsconfig.json` and update the `@cv` path to point to your CV file:

```json
{
  "compilerOptions": {
    "paths": {
      "@cv": ["./cv-en.json"]  // Change this to your CV filename
    }
  }
}
```

### 4. Run the Development Server

```bash
npm install
npm run dev
```

## 📋 CV Structure Guide

The `cv-example.json` file follows the [JSON Resume Schema](https://jsonresume.org/schema/) with the following sections:

### **basics** (Required)
Your personal information and contact details:
- `name`: Your full name
- `label`: Professional title/role (e.g., "Software Developer", "Systems Engineer")
- `email`: Contact email
- `phone`: Phone number with country code
- `summary`: Professional summary (3-5 sentences highlighting your expertise and experience)
- `location`: City and country
- `profiles`: Array of social profiles (LinkedIn, GitHub, etc.)

### **work** (Required)
Your work experience. **Design Limitation: Optimized for 3-4 experiences** for best single-page fit.

Each work entry includes:
- `name`: Company name
- `position`: Job title
- `startDate` / `endDate`: Format as "Month YYYY" or "present"
- `summary`: Array of 2-3 key achievements or responsibilities (focus on impact and results)
- `highlights`: Array of technologies and skills used (displayed as tags)

### **education** (Required)
Your educational background:
- `institution`: University or institution name
- `area`: Degree or major
- `studyType`: "Undergraduate", "Graduate", etc.
- `startDate` / `endDate`: Year format (YYYY)

### **skills** (Required)
Organized by categories (e.g., "Languages", "Technologies"):
- Each skill group has a `name` and `keywords` array
- Technologies are displayed as inline tags

### **competencies** (Optional but Recommended)
Soft skills and technical competencies:
- Mix of soft skills (Collaboration, Leadership) and technical competencies (Microservices Architecture, Performance Optimization)
- Displayed as inline tags in the right column

### **volunteering** (Optional)
Volunteer work and community involvement:
- `organization`: Organization name
- `position`: Your role (e.g., "Mentor", "Tutor")

### **Unused Sections**
The following sections are available in the schema but currently not displayed in the template:
- `awards`, `certificates`, `publications`, `interests`, `languages`, `projects`, `references`

You can leave these as empty arrays `[]` in your JSON file.

## ⚠️ Design Limitations

To maintain the single-page layout and optimal readability:

1. **Work Experience**: Best with **3-4 entries**. More than 4 may cause overflow or require font size reduction.
2. **Summary per Job**: Limit to **2-3 bullet points** per work experience.
3. **Professional Summary**: Keep to **3-5 sentences** (approximately 100-150 words).
4. **Skills & Technologies**: While there's no hard limit, excessive entries may wrap awkwardly. Aim for **10-15 key technologies**.
5. **Competencies**: Recommended **8-12 items** for balanced display.

## 🎨 Layout Structure

```
┌─────────────────────────────────────────┐
│           Header (Full Width)           │
│     Name, Title, Contact, Profiles      │
├──────────────────────┬──────────────────┤
│   Left Column (60%)  │ Right Column (40%)│
│                      │                  │
│  • Profile Summary   │  • Skills        │
│  • Work Experience   │  • Education     │
│                      │  • Competencies  │
│                      │  • Volunteering  │
└──────────────────────┴──────────────────┘
```

## 🌐 Multi-Language Support

To create CVs in multiple languages:

1. Create separate JSON files: `cv-en.json`, `cv-es.json`, etc.
2. Update the corresponding page files:
   - `src/pages/index.astro` imports from `cv-es.json` (Spanish)
   - `src/pages/en/index.astro` imports from `cv-en.json` (English)
3. Each page can be accessed at different URLs:
   - Spanish: `http://localhost:4321/`
   - English: `http://localhost:4321/en/`

## 📝 Tips for Best Results

- **Be Concise**: Every word counts on a single-page CV
- **Use Action Verbs**: Start bullet points with strong verbs (Developed, Implemented, Optimized)
- **Quantify Achievements**: Include numbers and metrics when possible
- **Prioritize Recent Experience**: Focus on your most recent and relevant roles
- **ATS-Friendly**: Avoid images, complex formatting, or tables that might confuse ATS systems
- **Proofread**: Check for typos and consistency in formatting

## 🙏 Credits

Format based on schema from: [JSON Resume Schema](https://jsonresume.org/schema/)

Idea inspired by: [Bartosz Jarocki - cv](https://github.com/BartoszJarocki/cv)

## 📄 License

Feel free to use this template for your own CV!
