# Request 2 (validated)

Rameen Kashif (456834) | Manal Aslam (465734) | Zainab Ali Bangash (486688)

> Deliver only the parcel for S2. What does it cost?

**Action (Act):** `plan_route({"algorithm": "astar", "heuristic": "tunnel_mst", "stops": ["S2"]})`

**Observation (Sense):** `{"ok": true, "algorithm": "astar", "heuristic": "tunnel_mst", "cost": 22.0, "steps": 13, "delivery_order": [{"stop": "S2", "step": 13}], "terrain_steps": {"road": 6, "grass": 3, "mud": 3, "ford": 1}, "ford_steps": [7], "stops": ["S2"], "avoid_terrain": [], "nodes_expanded": 70, "uses_tunnel": true}`

**Thought (Reason):** The delivery to S2 alone costs **22** (cheapest route found by A* with the tunnel-aware heuristic).

The route is 13 steps and uses one teleport tunnel. It crosses one ford at step 7, which the rival could flood if it opens the dam, so the cost could rise if that happens. I only planned the route and did not run a simulation.

**Final answer:**

The delivery to S2 alone costs **22** (cheapest route found by A* with the tunnel-aware heuristic).

The route is 13 steps and uses one teleport tunnel. It crosses one ford at step 7, which the rival could flood if it opens the dam, so the cost could rise if that happens. I only planned the route and did not run a simulation.