# Performance Testing — EduGenie AI Assistant

> ⚠️ This is a structured template, not filled-in results. Run the tool against your live server and record the real numbers — don't guess these.

## Step 1: Testing Overview

| Field | Details |
|---|---|
| Testing Tool Used | *[e.g., Locust, JMeter, or `k6` — Locust is easiest for a FastAPI app since it's also Python]* |
| Type of Testing | Load Testing (steady concurrent users) + Stress Testing (ramp until failure) |
| Target Module / API | `/qa`, `/explain/`, `/summarize/`, `/quiz`, `/learn/recommendations` |
| Test Environment | *[Local machine / cloud-hosted instance — specify]* |
| Test Date | *[Fill in]* |

## Step 2: Test Scenarios

| S.No | Test Scenario / Description | No. of Virtual Users | Duration (sec) | Expected Outcome |
|---|---|---|---|---|
| 1 | Baseline load on `/qa` (cloud route) | 10 | 60 | All requests succeed within timeout, avg response < 2s |
| 2 | Baseline load on `/explain/` (local route) | 10 | 60 | All requests succeed; response begins within 5s on 4GB RAM |
| 3 | Concurrent quiz generation on `/quiz` | 20 | 60 | JSON parses successfully for all responses, no schema failures |
| 4 | Stress test — ramp to failure across all routes | 50→200 (ramping) | 120 | Identify the concurrent-user ceiling before error rate exceeds 1% |

## Step 3: Performance Test Results

| S.No | Metric | Target Value | Actual Value | Status (Pass/Fail) | Remarks |
|---|---|---|---|---|---|
| 1 | Response Time (Avg) | < 2 seconds | *[Fill in]* | | Cloud routes depend on Gemini API latency |
| 2 | Response Time (Max) | < 5 seconds | *[Fill in]* | | |
| 3 | Throughput (Req/sec) | *[Fill in]* | *[Fill in]* | | |
| 4 | Error Rate | < 1% | *[Fill in]* | | |
| 5 | CPU Utilization | < 80% | *[Fill in]* | | Watch local-model route (`/explain/`) closely — most CPU-intensive |
| 6 | Memory Utilization | < 80% | *[Fill in]* | | LaMini-Flan-T5 weights (~3GB) held in memory once loaded |

## Step 4: Observations & Analysis
*[After running the load test, note anything interesting — e.g., "the local `/explain/` route became the bottleneck under concurrent load because the model isn't batched," or "cloud routes were rate-limited by the Gemini API tier after N req/min."]*

## Step 5: Screenshots / Evidence
*[Attach Locust/JMeter/k6 report screenshots here]*
