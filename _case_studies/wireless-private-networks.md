---
layout: page
title: "Wireless & Private Networks"
---

## The Challenge

Customers were experiencing real-time performance issues on private
network deployments, and the root cause — timing synchronization — was
poorly understood outside the engineering team.

Without [PTP (Precision Time Protocol)](https://docs.celona.io/en/articles/10581128-celona-ptp-guidelines-and-best-practices),
a site falls back to standard network timing like NTP, which introduces
microscopic clock drift. Milliseconds of drift are invisible to humans,
but they cause severe, immediate system failures for on-site end users.
When a cell tower site loses PTP or relies on a lower-tier timing
protocol, adjacent base stations drift out of phase, causing:

- **Dropped calls during handovers** — as a customer drives between two
  cell towers, mismatched timing prevents a clean transition, dropping
  the call or freezing the data stream.
- **Severe data slowdowns** — modern 5G uses Time Division Duplexing
  (TDD), where upload and download traffic share the same frequency but
  alternate by microseconds. Without PTP, upload and download signals
  collide, producing erratic speeds, packet loss, and "dead zones" even
  with full signal bars.

## My Process

I worked with product managers and solution architects to understand
the root cause of the problem, then researched why PTP is essential in
5G TDD networks. From there, I framed a document outline and wrote the
guide using concrete examples and diagrams to make an abstract timing
concept tangible for a non-RF-engineer audience.

## The Work

[Celona PTP Guidelines and Best Practices](https://docs.celona.io/en/articles/10581128-celona-ptp-guidelines-and-best-practices)

## Outcome

- Became one of the most consistently visited documents in the
  knowledge base
- Adopted by product engineers as the standard reference handed to
  support engineers
- Used directly by sales engineers to explain PTP's importance to
  customers during deployment conversations