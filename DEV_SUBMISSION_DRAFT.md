---
title: I Built StudyNest to Make Scattered Study Notes Easier to Review
published: false
tags: devchallenge, weekendchallenge, hf26challenge
---

## What I built

StudyNest is a small Vietnamese study companion for someone reviewing scattered notes. You can save notes in the browser, ask a question grounded in them, generate five practice questions with suggested answers, or get a short summary.

I built this during the Hacktoberfest Weekend Challenge. I tested it myself with a Python lesson note: when I asked why `ket_qua` was 34, it explained that `append(10)` changed `[7, 8, 9]` to `[7, 8, 9, 10]`, whose sum is 34. I have not yet handed it to another person, so I cannot claim feedback from a friend.

## Why open AI matters here

StudyNest uses the open-weight `openai/gpt-oss-20b` model through Groq's API. I can switch the model in a local configuration file without changing the study workflow. This also lets the app run without downloading a large model onto a computer with limited disk space. The app sends notes to Groq only when an AI feature is used; notes are stored in the browser's localStorage.

## How it works

The front end is one HTML file. A small Python HTTP server serves it and calls Groq through the official Python SDK. The server asks the model to answer only from the supplied notes and to say when the notes do not contain an answer. The API key stays in `config.py`, which Git ignores; `config_example.py` shows the configuration format.

## Demo

Live demo (temporary; available while the host computer and tunnel are running): https://carriers-intl-raid-salmon.trycloudflare.com

The demo has a shared limit of 30 AI requests per hour. Notes are stored in each visitor's browser and sent to Groq when an AI feature is used.

## Source code

https://github.com/AIVIETNAM-AIO-felixdoit/hacktobefest2026-challenge1

## What I learned and what comes next

My first local-model version required a download that did not fit the available disk space. Moving inference to Groq made the prototype usable on that machine, while keeping an open-weight model at its core. A future version should support exporting notes and let a learner answer quiz questions interactively.
