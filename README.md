# FamilyOS

FamilyOS is a shared space for a family’s important documents, deadlines, and events. Think of it as a family Google Drive with an AI organizer: upload a PDF, and FamilyOS reads and automatically groups it so everyone in the family can find it later.

Instead of searching through downloads, email attachments, and paper files, family members can keep household records together, ask questions about them, and stay on top of what is coming up.

## What you can do

- **Keep family documents together.** Upload PDFs to a shared family workspace so household records are in one place.
- **Upload by dragging and dropping.** Add one or more PDFs from the upload page. PDF files up to 10 MB are supported.
- **Let AI organize files.** FamilyOS processes uploaded PDFs and assigns them to categories such as finance, education, medical, housing, government benefits, and more.
- **Browse and open PDFs.** Find documents in their category folders, or search by filename or folder. Double-click a PDF in the document list to open it.
- **Invite family members.** Generate an invite code, choose a role for the person joining, and set how long the code lasts and how many times it can be used.
- **Manage family roles.** Family admins can manage members and assign roles, including admin, member, and child. Permissions vary by role; for example, child accounts cannot upload documents.
- **Track deadlines and events.** Add family deadlines, tasks, and upcoming events from the dashboard, then see them alongside recent uploads and missing-document reminders.
- **Ask questions about documents.** Use the AI chat to ask questions about information in your family’s uploaded files.
- **Reuse document information.** The companion Chrome extension can help autofill supported web forms with information from FamilyOS.

## How it works

1. Create an account and start a family workspace, or join one with an invite code.
2. Upload family PDFs.
3. FamilyOS processes each document and places it in a category.
4. Browse, search, or open documents; ask the assistant about their contents.
5. Invite family members and use the dashboard to keep track of deadlines and events.

## Built with

- **Frontend:** Next.js, React, and TypeScript
- **Backend:** FastAPI
- **Authentication, database, and file storage:** Supabase
- **AI features:** PDF text processing, document classification, document Q&A, and form autofill

## Project structure

- `frontend/` — FamilyOS web application
- `backend/` — FastAPI API and document processing
- `extension/` — Chrome extension for form autofill
- `shared/` — shared autofill schemas and contracts
- `supabase/` — database configuration and migrations

## Run locally

### Frontend

Configure `frontend/.env.local` with the Supabase URL and anon key, and the backend API URL:

```env
NEXT_PUBLIC_SUPABASE_URL=https://your-project.supabase.co
NEXT_PUBLIC_SUPABASE_ANON_KEY=your-anon-key
NEXT_PUBLIC_API_URL=http://127.0.0.1:8000
```

Then run:

```bash
cd frontend
npm install
npm run dev
```

### Backend

Create `backend/.env` with these backend environment variables, then install the dependencies and start the API:

```env
SUPABASE_URL=https://your-project.supabase.co
SUPABASE_SERVICE_KEY=your-service-role-key
SUPABASE_JWT_SECRET=your-jwt-secret
OPENAI_API_KEY=your-openai-api-key
```

The backend also accepts `OPENAI_LLM_API_KEY` or `OPENAI_RAG_API_KEY` in place of `OPENAI_API_KEY`. Run:

```bash
cd backend
pip install -r requirements.txt
uvicorn main:app --reload --port 8000
```

Never commit real API keys, service-role keys, or other secrets to the repository.
