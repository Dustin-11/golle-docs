# Glossary

### Action Key

Status assigned to a user’s step in the SMS workflow. Defines the current point in a sequential interaction. Examples: INITIAL, ASK_NAME, ASK_PASSENGERS, ONLINE, OFFLINE, APPROACHING_PICKUP.

### Async / Asynchronous

A process that occurs independently of the main execution flow, allowing the system to handle other tasks without waiting.

### API Contract

The defined structure of a request/response between services (endpoints, payload schema, headers). Ensures consistent communication between Golle services.

### Correlation ID

A unique identifier assigned to a user interaction that allows tracking across multiple services, messages, and steps in a workflow.

### Container Diagram

A C4 diagram showing the high-level architecture of the system, its containers (services, applications), and interactions.

### CRUD

Create, Read, Update, Delete. Standard operations for managing persistent data, such as ride requests.

### Dispatch Service

Handles driver matching, queuing ride requests, and sending notifications to riders and drivers through the Orchestration and SMS Gateway Service.

### IVR (Interactive Voice Response)

Telephony system used for rider payment onboarding, allowing users to provide payment information via phone prompts.

### IVR Onboarding

Capturing rider payment information through IVR to set up a saved payment method.

### Orchestration Service

Central service that coordinates workflows, routes messages between services, prompts users for next action steps, and handles sequential SMS interactions.

### OTP (One-Time Password)

Short-lived numeric code sent to a user’s phone to verify identity or phone number ownership.

### Non-blocking

Communication or tasks that occur independently of the main flow; e.g., async driver matching via the Dispatch Service.

### Rider / Driver

Users of the Golle Platform. Riders request rides; drivers accept rides, confirm pickups/dropoffs, and update status.

### Ride Request Service

Captures and manages ride request data. Ensures sequential validation and maps workflows to action keys.

### Retry Logic

Automatically attempts operations again if transient failures occur (e.g., network errors).

### SMS Gateway Service

Receives payloads from SMS providers, correlates phone numbers, assigns correlation IDs, converts payloads to match the Orchestration Service API contract, and forwards them for processing.

### SMS Provider / 3rd-Party SMS Provider

External service delivering SMS messages between riders/drivers and Golle (e.g., Twilio).

### Stateless

Service that does not maintain session state between requests; all context is passed through payloads.

### System Boundary

Defines the system’s components and separates them from external actors/services.

### Payment Service

Handles rider payments via IVR onboarding and triggers payment processing through an external processor like Stripe.

### Payment Processor

External service that executes financial transactions

### Third-Party API / External Service

Any service not built by Golle, used for core functionality like SMS delivery, payment processing, or location services.

### Twilio

Example SMS/IVR provider used in Golle MVP (replaceable with other providers).

### Webhook

A mechanism where an external system calls a registered URL endpoint with a JSON payload to notify the system of an event. Used by SMS providers to forward messages to the SMS Gateway.

### Worker

Process handling queued tasks asynchronously (e.g., Dispatch Service worker for driver matching).

### Appendix Notes

**Async vs. Non-blocking:** Async = tasks run independently. Non-blocking = service continues other work without waiting.

**Action Key Granularity:** SMS workflows require fine-grained keys. Web/mobile may only use the final key if state is locally maintained.

**Workflow Iteration:** Services like Ride Request may require multiple interactions with Orchestration until a valid ride request is completed.