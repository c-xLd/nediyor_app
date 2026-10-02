# Technical Architecture

Web ve mobile mevcut backend/API'yi paylaşmalıdır.

UI authoritative business logic hesaplamaz. Scoring ve AI server-side olmalıdır.

Domain boundaries:
Product, Search, AI, Price, Community, User.

Backend:
routes → services → repositories → validators → source adapters → AI orchestration → scoring → cache.

External integrations adapter üzerinden izole edilir. Secrets client'a çıkmaz.