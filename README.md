# Typex

Fullstack project combining a Next.js + Tailwind CSS frontend and an Express.js + MongoDB backend.

## Project Structure

```
/typex
├── /client        # Next.js app
├── /server        # Express.js API
├── .env.example   # sample environment for server
├── README.md
```

## Prerequisites

- Node.js 18 or later
- MongoDB instance for the backend

## Installation

Install all dependencies for both client and server:

```bash
npm run install:all
```

## Running Development Servers

### Backend only

```bash
cd server
npm run dev
```

### Frontend only

```bash
cd client
npm run dev
```

### Run both concurrently

From the project root:

```bash
npm run dev
```

This uses `concurrently` to start the Express server and Next.js app at the same time.

## Environment Variables

### Server `.env`
Copy `.env.example` to `.env` in the `/server` folder and fill in your values.

```
PORT=5000
MONGO_URI=mongodb://localhost:27017/typex
JWT_SECRET=yourStrongSecret
OPENAI_API_KEY=...
SUNO_API_KEY=...
SERPER_API_KEY=...
```

### Client `.env.local`
Create a `.env.local` file in `/client` with:

```
NEXT_PUBLIC_API_URL=http://localhost:5000/api
```

Adjust the URL when deploying so the frontend can reach the deployed backend.

## Deployment

### Frontend to Vercel
1. Push the repository to GitHub.
2. Import the project in Vercel and set the root directory to `client`.
3. Add environment variables from `client/.env.local`.
4. Set the build command to `npm run build` and the output directory to `.next`.

### Backend to Render/Railway
1. Create a new web service from your repository and point the root to `server`.
2. Add the environment variables listed in `.env.example`.
3. Set the start command to `npm start` or your custom start script.
4. Ensure CORS is configured to allow requests from your deployed frontend domain.

Once deployed, update `NEXT_PUBLIC_API_URL` on the frontend to the deployed backend URL.

## License

MIT
