# Request 9 (validated)

Rameen Kashif (456834) | Manal Aslam (465734) | Zainab Ali Bangash (486688)

> Plan with greedy best-first search and with A*. Which is cheaper and by how much? Keep the cheaper one as the current plan.

**Action (Act):** `plan_route({"algorithm": "greedy", "heuristic": "tunnel_mst"})`

**Observation (Sense):** `{"ok": true, "algorithm": "greedy", "heuristic": "tunnel_mst", "cost": 132.0, "steps": 51, "delivery_order": [{"stop": "S2", "step": 11}, {"stop": "S4", "step": 26}, {"stop": "S3", "step": 38}, {"stop": "S1", "step": 51}], "terrain_steps": {"grass": 16, "ford": 7, "mud": 13, "road": 15}, "ford_steps": [2, 7, 9, 13, 15, 38, 45], "stops": ["S1", "S2", "S3", "S4"], "avoid_terrain": [], "nodes_expanded": 64, "uses_tunnel": true}`

**Action (Act):** `plan_route({"algorithm": "astar", "heuristic": "tunnel_mst"})`

**Observation (Sense):** `{"ok": true, "algorithm": "astar", "heuristic": "tunnel_mst", "cost": 111.0, "steps": 61, "delivery_order": [{"stop": "S1", "step": 19}, {"stop": "S3", "step": 32}, {"stop": "S4", "step": 44}, {"stop": "S2", "step": 61}], "terrain_steps": {"road": 31, "grass": 16, "mud": 11, "ford": 3}, "ford_steps": [25, 32, 55], "stops": ["S1", "S2", "S3", "S4"], "avoid_terrain": [], "nodes_expanded": 3436, "uses_tunnel": true}`

**Action (Act):** `plan_route({"algorithm": "astar", "heuristic": "tunnel_mst"})`

**Observation (Sense):** `{"ok": true, "algorithm": "astar", "heuristic": "tunnel_mst", "cost": 111.0, "steps": 61, "delivery_order": [{"stop": "S1", "step": 19}, {"stop": "S3", "step": 32}, {"stop": "S4", "step": 44}, {"stop": "S2", "step": 61}], "terrain_steps": {"road": 31, "grass": 16, "mud": 11, "ford": 3}, "ford_steps": [25, 32, 55], "stops": ["S1", "S2", "S3", "S4"], "avoid_terrain": [], "nodes_expanded": 3436, "uses_tunnel": true}`

**Thought (Reason):** A* is cheaper. Both plans used the same heuristic (tunnel_mst) and covered all four stops.

- **Greedy best-first:** cost 132, 51 steps, 64 nodes expanded. Delivery order: S2, S4, S3, S1.
- **A\*:** cost 111, 61 steps, 3,436 nodes expanded. Delivery order: S1, S3, S4, S2.

A* is cheaper by 21 cost units. It is now the current plan, and I re-planned it last so it is the active route.

The A* route crosses fords at steps 25, 32 and 55. S3 is itself a ford, so the stop at step 32 sits on a ford. If the rival opens the dam, those fords flood for 15 steps. I have not simulated the route yet.

**Final answer: the A\* plan is the one to run, with total cost 111.**

**Final answer:**

A* is cheaper. Both plans used the same heuristic (tunnel_mst) and covered all four stops.

- **Greedy best-first:** cost 132, 51 steps, 64 nodes expanded. Delivery order: S2, S4, S3, S1.
- **A\*:** cost 111, 61 steps, 3,436 nodes expanded. Delivery order: S1, S3, S4, S2.

A* is cheaper by 21 cost units. It is now the current plan, and I re-planned it last so it is the active route.

The A* route crosses fords at steps 25, 32 and 55. S3 is itself a ford, so the stop at step 32 sits on a ford. If the rival opens the dam, those fords flood for 15 steps. I have not simulated the route yet.

**Final answer: the A\* plan is the one to run, with total cost 111.**