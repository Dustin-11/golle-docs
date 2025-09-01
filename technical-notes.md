# Technical Notes

## Architecture Highlights

* **Centralized Orchestration:** Ensures consistent workflows for sequential SMS prompts.
* **Action Key State Management:** Tracks per-user state across multiple asynchronous interactions.
* **Phone Authorization & Security:** OTP validation, phone number state tracking, and security checks.
* **Async Dispatch:** Drivers are matched via queue workers; notifications flow through orchestration to SMS Gateway.
* **Webhook Standardization:** SMS Gateway normalizes third-party payloads to Golle’s API contract.
* **Error Handling & Logging:** Retry logic for network errors, centralized logging for observability.

## Scalability Considerations

* Stateless communication over SMS allows horizontal scaling.
* Microservices enable future addition of web/mobile clients without changing core SMS workflows.
* Orchestration service designed to be fast, reliable, and easily debuggable.

## Extensibility / Future Enhancements

* Multi-channel support (Web/Mobile) with same action key logic.