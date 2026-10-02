# API Contract

JSON, typed schemas, stable errors, pagination, timestamps, cache metadata ve source freshness.

Core:
GET /api/home
GET /api/search
GET /api/products/:slug
GET /api/products/:slug/mentions
GET /api/products/:slug/sources
GET /api/products/:slug/price
GET /api/products/:slug/alternatives
POST /api/products/:slug/questions
GET /api/deals
GET /api/compare
GET /api/watchlist
POST /api/watchlist
POST /api/price-alerts

Errors: code, message, requestId. Stack trace expose edilmez.