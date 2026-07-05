# Won Woo

**Frontend / Product Engineer**  
Boundary-first frontend architecture for business-critical products.

I design frontend systems where product impact depends on rendering stability, lifecycle control, operational efficiency, and measurable user behavior.

My main focus is not just building screens.  
I focus on defining the right boundaries before the product grows too large to control.

---

## Core Positioning

I work across:

- **Hybrid WebView Systems**
- **Business-Critical Frontend**
- **React / Next.js / React Native**
- **Ad, Reward, and Conversion Flows**
- **AI/LLM Product Execution**
- **Mobile Productization**

I have built and operated frontend systems in financial, healthcare, commerce, reward, and AI product domains.

---

## Architecture Philosophy

### Boundary-First Frontend

I believe frontend architecture begins before component design.

A screen is only the output.  
The real system is made of boundaries.

The boundaries I define first:

- **Routing / Navigation Boundary**  
  What belongs to a page, a flow, a modal, a tab, or a full-screen transition.

- **Server State / Client State Boundary**  
  What comes from the server, what belongs to user interaction, and what must survive rendering changes.

- **Domain / UI Boundary**  
  What is product-specific logic and what should become reusable interface infrastructure.

- **External SDK / Internal Runtime Boundary**  
  External SDKs are not just libraries.  
  They are runtimes with their own loading, initialization, rendering, failure, and recovery behavior.

- **Loading / Error / Empty / Fallback Boundary**  
  Failure states should be designed as part of the product flow, not patched after bugs appear.

- **Operation / Deployment Boundary**  
  Product operations should not always require app deployment.  
  Frontend systems should expose safe control points for campaign, content, and business operation.

Good frontend architecture is not about making folders look clean.  
It is about making the next change obvious.

---

## Selected Engineering Work

### Business-Critical Frontend Runtime

At KB Kookmin Bank, I worked on frontend systems for ad, benefit, and reward surfaces inside a large-scale mobile banking environment.

The challenge was not simply rendering banners.  
The real problem was controlling a business-critical frontend runtime inside a hybrid WebView environment.

I structured the frontend flow around:

- Ad request lifecycle
- Response normalization
- Type-based rendering policy
- Impression timing
- Skeleton and layout stability
- No-fill handling
- External SDK fallback
- UI post-processing
- WebView re-entry stability

This reduced repeated ad integration work from a multi-day task to a reusable system-level workflow.

---

### Hybrid WebView Lifecycle Stability

Hybrid WebView environments fail in ways that ordinary web apps often do not.

I have worked through issues involving:

- App re-entry
- Pull to Refresh
- stale rendering
- duplicate render requests
- external SDK initialization timing
- iframe-based isolation
- layout collapse
- native/web lifecycle mismatch

For ad SDK integration, I treated the SDK as an external runtime rather than a simple dependency.

Key implementation patterns included:

- Promise-based SDK initialization control
- container-level instance management
- stale render prevention
- render completion detection
- fallback policy separation
- preserve vs refresh rendering strategy
- layout height stabilization before and after render

The goal was not only to make the ad appear.  
The goal was to make rendering predictable under unstable real-world app lifecycle conditions.

---

### `useAd` Common Ad Module

I designed and implemented a common frontend module for ad rendering and fallback control.

The module unified:

- DMP ad request
- response schema normalization
- banner / icon / swiper / button / card rendering
- no-fill handling
- impression event handling
- external SDK fallback
- skeleton and layout policy
- WebView re-entry behavior

The important decision was to stop treating each ad surface as an isolated screen task.

Instead, I treated ads as a frontend runtime with its own lifecycle, state transitions, and failure recovery path.

```ts
DMP Request
  -> Normalize Response
  -> Render by Type
  -> Detect Exposure
  -> Send Impression
  -> Handle No-fill
  -> Fallback Runtime
  -> Stabilize Layout
