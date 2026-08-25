# Revenue Rescue AI — System Architecture

## 1. Overview

Revenue Rescue AI is an event-driven AI revenue recovery system designed to identify failed payment recovery opportunities, determine appropriate interventions, execute bounded recovery actions, and automatically stop recovery workflows when payment succeeds or safety limits are reached.

## 2. High-Level Architecture

Razorpay Test Mode
        ↓
Webhook Receiver
        ↓
Make.com Event Router
        ↓
Supabase State + Memory
        ↓
Dify AI Recovery Agent
        ↓
Deterministic Policy Engine
        ↓
Recovery Action
        ↓
Payment Status Observation
        ↓
Supabase
        ↓
Merchant Dashboard

## 3. Core Events

- payment.failed
- payment.captured

## 4. AI Responsibilities

The AI agent may determine:

- Recovery probability
- Priority
- Recommended channel
- Recommended timing
- Recovery strategy
- Escalation recommendation

## 5. Deterministic Controls

AI recommendations are subject to deterministic policy controls including:

- Payment-success stopping
- Maximum recovery attempts
- Customer opt-out handling
- High-value transaction escalation
- Invalid AI-output fallback
- Channel fallback
- Duplicate event protection

## 6. Persistent State

Supabase stores:

- Customers
- Payments
- Recovery cases
- Recovery actions
- Recovery outcomes
- Audit events

## 7. Evaluation

The system will be evaluated using synthetic payment events and compared against a generic recovery baseline.

Primary metrics:

- Recovery rate
- Incremental recovered revenue
- Recovery time
- Intervention count
- Communication cost
- Recovery efficiency

## 8. Security

Secrets must never be committed to GitHub.

Webhook authenticity, event idempotency, access control, and safe AI execution are core engineering requirements.
