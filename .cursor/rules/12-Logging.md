---
description: Structured logging conventions
globs: src/**/*
alwaysApply: false
---

# Logging

## Backend

`ILogger<T>` · structured params (no interpolation) · correlation ID per request

Levels: Debug (dev) · Information (events) · Warning · Error · Critical

## Frontend

Console in dev only · no sensitive data in browser logs

## Log / Don't Log

Request duration, business events, sanitized validation failures / passwords, tokens, PII, connection strings

## Forbidden

`Console.WriteLine` in prod BE · secrets in logs · empty catch without log
