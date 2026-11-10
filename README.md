# Case study: outbound AI voice agent

This repo is a write-up only. The code, prompts and data belong to the client and are not included.

## The problem

An Australian B2B sales team needed an AI agent to call leads, ask qualifying questions and save the results to their CRM.

## Results

- First live call 3 days after I started.
- 440+ unique lead calls in production within 4 weeks.
- Every call scored automatically, and results sent to the client's Zoho CRM.
- The client gained 14 new clients.

## Architecture

- Python and FastAPI, with Twilio for calls.
- Four voice setups, switchable per account without redeploying: Gemini Realtime, a Deepgram-managed voice agent, a custom speech-to-text, LLM and text-to-speech pipeline, and an ElevenLabs agent.
- Background workers run the call queue, with retries.
- After each call, a separate AI step extracts pain points and business size, scores the call on professionalism, qualification and listening, and pushes the result to Zoho CRM through a webhook.
- A Zoho workflow adds new leads to the call queue.
- Docker and Nginx, PostgreSQL, a login with rate limits, and a dashboard where prompts can be edited without a restart.

## What I built and what I used off the shelf

- **Built:** pipeline switching, call queue and retry logic, carrier-error handling, timezone routing, SMS replies, post-call scoring, CRM sync.
- **Off the shelf:** Gemini, Deepgram and ElevenLabs models, Twilio, Zoho, PostgreSQL.

## How I worked

I designed the system and chose how the pieces connect. I wrote the code with AI coding assistants, then reviewed and tested it.

## A related public project

[Voice-agent](https://github.com/VinayNarne/Voice-agent) is a smaller voice assistant I built on the Azure OpenAI Realtime API, with its code and tests in the open.
