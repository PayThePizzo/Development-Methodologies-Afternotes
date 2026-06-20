# Fortnite

The delay before data begins to transfer after a request is
made. Minimizing latency is critical for real-time
applications like gaming or video streaming.

Example: In online gaming, high latency causes lag,
disrupting the user experience. Techniques to reduce
latency include reducing network hops and optimizing
backend processing times.

Fortnite’s Architecture:
– Microservices-Based Backend:
• Uses Kubernetes to scale services such as matchmaking and account management.
– SaaS Integration:
• OAuth2 support for logins with Google, PlayStation Network, and Xbox Live accounts.
• SaaS payment systems to handle microtransactions.
– Cross-Platform Play:
• Players on consoles, PCs, and mobile devices can play together.
• Cloud synchronization for progress and purchases.

Results:
– Millions of simultaneous players.
– Service continuity even during global updates, thanks to distributed systems.
– Effective monetization with personalized in-game purchases.

Concurrent Users (peak): 15.3M+ (during
special events).
Concurrent Users (daily average): Millions of
wolrdwide players.
Monthly Active Users (MAU): 350M registered
users.

Client-server calls per second:
– Matchmaking and authentication: 100.000+ of
requests per second during peak
– WebSocket and Real-Time updates: 30.000+
messages per second per game server.

Latency: 20-50ms for most players using
regionally distributed servers.

Game severs in operation: 1000+ of server
instance on cloud providers.
– Each server suppors 100-200 players per match
DB queries for player profiles: 2M+ of queries
per day.
Logged Events: 2TB+/daily for every player.
CDN: handling 2PB+ of monthly traffic.
Cost per player: about $0.01 per player per day
on cloud infrastructure, depending on global
demand