# Request 16 (validated)

Rameen Kashif (456834) | Manal Aslam (465734) | Zainab Ali Bangash (486688)

> Plan a route for all four stops with total cost under 100.

**Action (Act):** `plan_route({"algorithm": "astar", "heuristic": "tunnel_mst"})`

**Observation (Sense):** `{"ok": true, "algorithm": "astar", "heuristic": "tunnel_mst", "cost": 111.0, "steps": 61, "delivery_order": [{"stop": "S1", "step": 19}, {"stop": "S3", "step": 32}, {"stop": "S4", "step": 44}, {"stop": "S2", "step": 61}], "terrain_steps": {"road": 31, "grass": 16, "mud": 11, "ford": 3}, "ford_steps": [25, 32, 55], "stops": ["S1", "S2", "S3", "S4"], "avoid_terrain": [], "nodes_expanded": 3436, "uses_tunnel": true}`

**Action (Act):** `tunnel_info({})`

**Observation (Sense):** `{"pairs": [[[0, 5], [9, 2]], [[12, 0], [13, 10]], [[12, 4], [12, 17]]], "cost_per_jump": 1.0}`

**Action (Act):** `flood_status({})`

**Observation (Sense):** `{"dam_used": false, "flood_steps_left": 0, "flood_duration": 15, "stops_that_need_a_ford": ["S2", "S3"], "stop_cells_that_are_fords": ["S3"], "current_plan_ford_steps": [25, 32, 55]}`

**Action (Act):** `plan_route({"algorithm": "ucs", "heuristic": "zero"})`

**Observation (Sense):** `{"ok": true, "algorithm": "ucs", "heuristic": "zero", "cost": 111.0, "steps": 61, "delivery_order": [{"stop": "S1", "step": 19}, {"stop": "S3", "step": 32}, {"stop": "S4", "step": 44}, {"stop": "S2", "step": 61}], "terrain_steps": {"road": 31, "grass": 16, "mud": 11, "ford": 3}, "ford_steps": [25, 32, 55], "stops": ["S1", "S2", "S3", "S4"], "avoid_terrain": [], "nodes_expanded": 5187, "uses_tunnel": true}`

**Action (Act):** `plan_route({"algorithm": "astar", "heuristic": "tunnel_mst", "avoid_terrain": ["ford"]})`

**Observation (Sense):** `{"ok": false, "validation_errors": ["infeasible: S3 (22, 17) is itself a ford cell, so it cannot be delivered while avoiding ford"]}`

**Thought (Reason):** I couldn't find a route under 100. The cheapest route for all four stops costs **111**, so the request can't be met as stated. I haven't run the simulation, since it would execute an over-budget plan.

- **A* (tunnel_mst heuristic)** returned a route costing 111 in 61 steps.
- **Uniform-cost search**, which is optimal without a heuristic, also returned 111, so 111 appears to be the minimum over all delivery orders.
- **Avoiding fords** is infeasible, because S3 at (22, 17) is itself a ford cell.

The cheapest route is: S1 at step 19, S3 at step 32, S4 at step 44, S2 at step 61. It uses 31 road, 16 grass, 11 mud and 3 ford steps, and it takes one teleport tunnel.

To get under 100, the stop set or the budget would need to change. For example, dropping S2 at (0, 1), the farthest stop, would likely bring the cost down, but I haven't checked that.

**Final answer:**

I couldn't find a route under 100. The cheapest route for all four stops costs **111**, so the request can't be met as stated. I haven't run the simulation, since it would execute an over-budget plan.

- **A* (tunnel_mst heuristic)** returned a route costing 111 in 61 steps.
- **Uniform-cost search**, which is optimal without a heuristic, also returned 111, so 111 appears to be the minimum over all delivery orders.
- **Avoiding fords** is infeasible, because S3 at (22, 17) is itself a ford cell.

The cheapest route is: S1 at step 19, S3 at step 32, S4 at step 44, S2 at step 61. It uses 31 road, 16 grass, 11 mud and 3 ford steps, and it takes one teleport tunnel.

To get under 100, the stop set or the budget would need to change. For example, dropping S2 at (0, 1), the farthest stop, would likely bring the cost down, but I haven't checked that.