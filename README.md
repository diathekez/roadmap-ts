# 100Devs Roadmap

This is a roadmap voting app built with TypeScript and Next.js that's deployed on Vercel. It uses Upstash for the DB and next-auth for authentication.

**Link to project:** https://100devs-roadmap.vercel.app/

![Roadmap landing page](https://raw.githubusercontent.com/diathekez/roadmap-ts/master/public/docs/landing-page.png)

## Technologies

**TypeScript, Next.js, Upstash**

The minimalist nature of this roadmap voting app makes it versatile and easily customizable. I took it from a template on Vercel and did some tinkering with it. The template comes with docs, but they're outdated, so I wrote an updated version.

## Optimizations

Currently, you're only allowed to vote up. You can't take your vote back or vote down. I'm not sure if people should be able to vote down, but I'll add the voting up ability later.

---

## Installation

1. [Project Set Up](#1-project-set-up)
2. [Environment Variables Configuration](#2-environment-variables-configuration)
3. [Database](#3-database)
4. [User authentication with next-auth](#4-user-authentication-with-next-auth)
5. [Running the project](#5-running-the-project)
6. [Admin Permissions](#6-admin-permission)
7. [Deploying to Vercel](#7-deploying-to-vercel)

## `1` Project Set Up

Clone this repo or download the zip and drop it on your code editor. On your terminal, run:

```
npm install
```

## `2` Environment Variables Configuration

Duplicate the `.env.local.example` file and name it `.env.local` (which
will be ignored by Git).

## `3` Upstash Database

Go to the [Upstash Console](https://console.upstash.com/) and create a new
database.

#### Upstash environment

`UPSTASH_REDIS_REST_URL` and `UPSTASH_REDIS_REST_TOKEN` find the variables in
the database details page in Upstash Console.

**IMPORTANT**
Make sure you scroll down a bit until you see the `REST API` section. Copy those two items, not the endpoint and password.

## `4` User Authentication with next-auth

We will use the **[next-auth](https://next-auth.js.org/)** library for authentication. This repo is preconfigured to use GitHub OAuth.

To set up GitHub for authentication:

1. Go to [GitHub Developer Settings](https://github.com/settings/apps) on
   GitHub.

2. On the left panel, click **OAuth Apps** and then click **"New GitHub App."**

3. Give your app a name.

4. Add your **"Homepage URL"** (you can use a placeholder of any website).

5. For the **"Callback URL"** field, put http://localhost:3000.

6. If the active field under "Webhook" is checked, uncheck it. Now, click on **"
   Create Github App."**

7. Once your app is created, you should see the following screen. Click on **"
   Generate a new client secret."**

8. Copy the client secret you generated and paste it under the `GITHUB_SECRET`
   value in your .env file

9. Copy the **Client ID** and paste it under the `GITHUB_ID` value in your .env
   file

## `5` Run the Project

In the project folder, run

```
npm run dev
```

## `6` Admin Permissions

Only admin users can delete and release content.

`NEXT_PUBLIC_ADMIN_EMAILS`: Enter GitHub emails here, separated by commas.

## `7` Deploy to Vercel

First, create a new Github repository and push your local changes.

[Deploy it to Vercel](https://vercel.com/docs/concepts/git#deploying-a-git-repository)

Make sure you manually add all [Environment Variables](https://vercel.com/docs/concepts/projects/environment-variables) in your .env file to Vercel during the import process.
