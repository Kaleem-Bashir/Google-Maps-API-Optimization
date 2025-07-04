# 🧭 Google Maps Microservice API Optimization .NET Core

A highly efficient, scalable microservice built in **.NET Core**, designed to **wrap and optimize Google Maps APIs** (Places, Directions, Autocomplete) with intelligent caching, dynamic routing, and data-layer persistence.

✅ This service drastically reduced client-side Google Maps API expenses from **$3,000+ per month to under $100**, while maintaining **full feature parity** and improving speed & performance across millions of records.

---

## 🙋‍♂️ About Me

I specialize in backend engineering, API architecture, and cost-optimized solutions for enterprise clients. This project reflects my ability to **translate business problems into fast, scalable, and cost-efficient technical systems.**

---

## 💡 Problem Solved

The client’s systems made direct calls to Google Maps APIs for each user query. With scale, this led to:
- Excessive API billing (esp. from Places & Autocomplete)
- Redundant repeated requests
- No internal visibility or control
- Performance issues at scale

## 🧠 Additional features
-  🌍 Optional fallback to OpenStreetMap for pricing resilience
-  🔑 Admin dashboard for managing search hot zones
-  🧠 Add ML-based relevance scoring to results
-  📤 Offline export to GeoJSON / CSV

---

## 🛠️ What I Built

### 🔹 A .NET Core Microservice That:
- Proxies and **intelligently consumes Google Maps APIs**
- **Caches high-traffic queries** (like repeated location searches)
- **Persists enriched location data** in a custom structured store
- Handles **autocomplete**, **directions**, and **place details**
- Uses **rate limiting, response coalescing**, and **query hashing** to **minimize requests to Google**

---

## ⚙️ Key Technical Features

### ✅ .NET 8 Core Microservice Architecture
- Clean separation of concerns with **Clean Architecture principles**
- Fully async pipeline with **scoped DI**, **MediatR**, and **AutoMapper**
- **OpenAPI/Swagger** for testability

### 🧠 Intelligent Caching & Storage
- **Memory cache & Redis** layered architecture
- **Query fingerprints** (hashes) for exact-match lookup
- Results persisted in **SQL Server / PostgreSQL** with indexing on:
  - `PlaceId`
  - `Lat/Lng`
  - `Search Input`
- **Self-learning cache** — hot queries automatically persisted

### 📍 Google Maps API Usage (Indirect, Controlled)
- Wrapped:
  - `Autocomplete API`
  - `Directions API`
  - `Places Details API`
- All usage throttled, batched, and recorded
- Custom headers/params to support multiple tenants and users

### 📈 Scalability
- Handles **millions of location records**
- Horizontal scaling supported via Docker/K8s
- API-level sharding support via tenant context

---

## 📉 Business Outcome

| Metric                     | Before Optimization | After Optimization |
|----------------------------|---------------------|---------------------|
| Monthly Google Maps Cost   | $3,000+             | <$100               |
| API Response Time (avg)    | ~500ms              | ~80ms (cached)      |
| Duplicate Requests         | 1000s/day           | <1% (fully cached)  |
| Developer Control          | None                | Full control/logging|
| Brand Customization        | ❌                  | ✅                  |

---

## 🌐 API Endpoints
E.G
GET /api/maps/autocomplete?input=Statue of Liberty
GET /api/maps/place-details?placeId=ChIJ1bRlhQi3GTkRYi55HQfdkvw
GET /api/maps/directions?origin=A&destination=B



Each endpoint returns **Google-like accuracy** but is **cost-optimized, cached, and enriched**.

---

## 🏗️ Architecture Diagram (Simplified)

            +------------+
            |  Client UI |
            +------------+
                  |
                  v
          +----------------+
          |  .NET Core API |
          +----------------+
                  |
      +------------------------+
      |    Google Maps APIs    |
      +------------------------+
                  |
          +----------------+
          |   Caching DB   | <-- Redis (hot queries)
          +----------------+
                  |
          +----------------+
          |      SQL        | <-- Long-term storage
          +----------------+



---

## 🔐 Security & Multi-Tenant Support

- API key–based authentication
- Custom tenant scoping (`x-tenant-id` headers)
- Rate limiting and abuse protection middleware

---

## 📍 Logging & Monitoring

- Integrated **Serilog** for:
  - Request tracing
  - Response time monitoring
  - Cache hit/miss logs
- Exposed to centralized log sinks (e.g., Seq, ELK)

---

