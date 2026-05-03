# Weather Integration

## Purpose

Adapter for weather data retrieval, used by the assistant core to answer weather-related queries.

## Responsibilities

- Fetch current and forecast weather data from a configured provider.
- Cache the most recent weather data to support graceful fallback when the provider is unavailable.
- Return structured data that the assistant core formats for spoken output.
- Disclose data freshness when serving from cache.

## Boundaries

**In scope:**
- Weather API integration (provider-agnostic via adapter interface).
- Local cache with configurable TTL.
- Structured response with forecast data and freshness metadata.

**Out of scope:**
- Spoken formatting (assistant core responsibility).
- User preference for location (handled via user profile).

## Local ADRs

Component-specific decisions are in `docs/adr/`.

## Status

Not yet implemented. See `docs/design/` for design notes.
