# Time-window itinerary solver

이동 시간·방문 가능 시간·체류·예산을 지키며 모든 방문을 마치는 최단 일정을 찾는다.

A focused executable resource for AI-assisted structured work. **Zero runtime dependencies, no API key, Node.js 22+.**

[Live workspace](https://proofnova.github.io/time-window-itinerary/) · [한국어 리소스 모음](https://proofnova.github.io/) · [Task contract](resource.json) · [Prior art](RESEARCH.md)

```sh
git clone https://github.com/proofnova/time-window-itinerary.git
cd time-window-itinerary
npm test
node cli.mjs example.json
```

## What it does

Bounded exact time-window search with waiting, asymmetric travel and explicit optimality.

Nearest-first routing can miss a closing window; search exhaustion cannot prove infeasibility.

## Connect a model

Import `execute` from `./run.mjs`. Expose this declared tool to your model, validate its tool name/input contract, execute it, and retain the returned JSON and input digest. Calculations and constraint checks are performed by the resource. No paid model or new agent framework is required.

[SKILL.md](SKILL.md) contains the workflow, interpretation and recovery procedure. [example.json](example.json) is a complete input; [cases.json](cases.json) contains worked and edge-case synthetic regression checks. The website executes the same code locally in a bounded Worker. It has no model or external data upload.

## Recovery and limits

Change the requested windows/travel data or budget when infeasible; do not fabricate live availability.

Underlying algorithms and task outcomes already exist in the alternatives. An existing tool configured for this exact task may remove the need for a separate project. Small synthetic tests cannot establish broad expertise or external demand. See [RESEARCH.md](RESEARCH.md). A plan/audit is not an external action or proof of actual user benefit.

## Contribute

Open an issue with a synthetic/redacted failing JSON input, expected result and Node version. Add a regression test and run `npm test`. Never include credentials or real private records in public examples.

MIT · Proofnova · 2026

## Measured worked-example comparison

See [workflow-benchmark.json](workflow-benchmark.json) for executed inputs, baseline algorithm and full output. Nearest-first misses stop b’s closing window; exact search completes both stops at minute 6. This is one synthetic worked example, not a model-accuracy result or a claim about typical real-world savings.
