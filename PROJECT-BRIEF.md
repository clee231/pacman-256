# Project direction

## Purpose

Create a polished, mobile-first browser game for a three-person AI workshop team. The project is both a playable game prototype and a demonstration of an intentional, collaborative AI-assisted engineering workflow.

This document records the direction agreed so far. It is product context, not an implementation plan or a commitment to a specific technology.

## Product concept

Build an original, arcade-style maze-chase game with real-time competitive multiplayer. Players compete to survive in a shared maze, with a small set of readable power-ups and a modern, stylized visual treatment.

Use original game naming, characters, maze layouts, art, audio, and other assets. The team can draw on the broad maze-chase genre, but should not use Pac-Man branding or copy its distinctive characters or assets.

## Direction agreed so far

| Area | Current direction |
|---|---|
| Audience and platform | Mobile-first web game, targeting mobile browsers; responsive layout is desired. |
| Core mode | Online, real-time versus play. |
| Match concept | Short survival rounds; players compete until one remains. Eliminated players spectate. |
| First match size | Start with up to 4 players. Treat 32 players as a possible later scalability goal, not an MVP requirement. |
| Match length | Aim for roughly 2–3 minutes. |
| Joining | Private rooms with a code or invite link first. Add quick play if time permits. |
| Controls | Must feel good on touch screens and adapt to device orientation. Exact control design remains open. |
| Power-ups | Start with a speed boost and a temporary shield. |
| Visuals | Simple, recognizable, modern stylized art; 2D gameplay with selective 3D depth or effects. |
| Theme | Deliberately undecided; choose an original setting with the team. |
| Business model | Sample/workshop project; no monetization planned. |
| Timebox | Three full days. Prioritize a complete, demonstrable match over breadth. |

## MVP outcome

The MVP should let a small group of players:

1. Open the game on a mobile browser and enter a private room.
2. Join the same match using a room code or invite link.
3. Use responsive touch controls to move through a shared maze.
4. Compete in one complete survival round, including the speed and shield power-ups.
5. See a clear round end and result, including the winner.

Room creation and joining are the first matchmaking slice. Quick play, accounts, public matchmaking, larger lobbies, and production-scale operations are not prerequisites for this outcome.

## Proposed implementation direction (not yet decided)

A browser-based TypeScript client with a game-focused rendering/interaction framework, plus a small real-time multiplayer service, is a reasonable starting point for the mobile-web goal. Phaser is one candidate for the client. The team should compare the simplest viable options against its experience, deployment needs, and the three-day timebox before choosing.

Before implementation, decide and record:

- Client framework and rendering approach.
- Multiplayer transport and whether the server is authoritative for movement, collisions, power-ups, and elimination.
- Hosting/deployment approach and how teammates will share a playable build.
- Room lifecycle, disconnect/reconnect behavior, and what happens if a room is not full.
- Device/browser test matrix and the minimum performance target.

Keep the game rules and network messages small and explicit. Avoid making a 32-player architecture, 3D production pipeline, account system, or complex matchmaking service a prerequisite for the first playable round.

## Open product decisions

- Original title, setting, character designs, maze style, and audio direction.
- Exact movement rules, collision behavior, and how players can affect or avoid each other.
- What the speed boost and shield do, how long they last, and how they are acquired.
- Whether a round starts when the room is full or after a short countdown.
- Touch-control layout, portrait/landscape behavior, accessibility options, and desktop fallback.
- How eliminated players spectate and how results are presented.
- Whether quick play is achievable after private rooms and a complete match work.

Resolve decisions in the order they affect the next playable increment. Record consequential changes so that product context and implementation do not drift apart.

## Suggested AI-first collaboration workflow

The workshop guide emphasizes that clear context, explicit specifications, task-sized planning, and human review have more leverage than generating code quickly. Use this brief as the shared product starting point, then keep the workflow lightweight and visible.

### Shared source of truth

- Keep product intent, constraints, terminology, and current decisions in version control.
- For each feature, write a short spec before implementation: user outcome, rules, acceptance criteria, edge cases, and how it will be tested.
- Record architecture choices as short decision notes, including the alternatives considered and why the team chose one.
- Update shared context when a decision changes; avoid relying on one person's chat history as project memory.

### Use AI in bounded, reviewable steps

1. Ask an AI assistant to clarify the problem and propose acceptance criteria before asking it to implement.
2. Have it outline a small plan that maps directly to the spec.
3. Delegate only independent, well-bounded work. Keep shared interfaces and integration decisions coordinated by a teammate.
4. Ask for focused tests with each behavior change, then run the checks and review the diff as humans.
5. Use a separate review pass to look for missed requirements, mobile usability issues, multiplayer edge cases, and regressions.
6. Require the implementer to report what changed, what was tested, and what remains uncertain.

### Suggested role split for three people

Treat these as rotating areas of ownership, not silos:

- **Product and game experience:** owns the rules/specs, touch interaction, and playtesting feedback.
- **Multiplayer and platform:** owns room lifecycle, real-time state flow, and deployment concerns.
- **Integration and quality:** owns shared contracts, end-to-end testing, and keeping the playable build and project context current.

Pair on architecture and integration points. Rotate who drives the AI workflow so that all three people can explain and demonstrate it.

### Demonstrate the workflow, not just the game

Keep a small trail of evidence the team can show: a feature spec and its acceptance criteria, a plan refined by human feedback, a bounded AI-assisted implementation, tests or a manual test record, and a review that caught or prevented a problem. The aim is to show that AI accelerated a well-directed engineering process—not that generated code was accepted without understanding.

## Scope guardrails

- Make a complete small match the success criterion; defer scale and polish that do not support it.
- Test on real target mobile browsers early, especially touch input and viewport behavior.
- Prefer original or properly licensed assets; do not assume workshop use grants rights to third-party game assets.
- Do not put credentials, private participant information, or other sensitive material into AI prompts.
- Treat AI output as a proposal. Team members remain responsible for design decisions, code, tests, and the demo.
