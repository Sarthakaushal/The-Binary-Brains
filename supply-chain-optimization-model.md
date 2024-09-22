# Distributor Crop Proposal Optimization Model

## Decision Variables
- $p_i$: Price to offer producers for crop $i$ (per kg)
- $l_i$: Logistics capacity allocated to crop $i$ (in m³)
- $t_i$: Shipping time for crop $i$ (in days)
- $y_i$: Binary variable, 1 if crop $i$ is included in the proposal, 0 otherwise

## Parameters
- $x_i$: Known demand for crop $i$ (in kg)
- $L_{total}$: Total available logistics capacity (in m³)
- $c_l$: Cost of logistics per unit volume ($/m³)
- $\rho_i$: Density of crop $i$ (kg/m³)
- $p_{min,i}$: Minimum acceptable price for crop $i$ (per kg)
- $t_{max}$: Maximum acceptable shipping time (in days)
- $s_i$: Selling price of crop $i$ to retailers (per kg)

## Objective Function
Maximize profit:
$$\text{Maximize } Z = \sum_{i=1}^n (s_i - p_i - c_l/\rho_i)x_i y_i$$

## Constraints
1. Logistics capacity:
   $$\sum_{i=1}^n l_i \leq L_{total}$$
   $$x_i y_i \leq \rho_i l_i \quad \forall i$$

2. Minimum price for producers:
   $$p_i \geq p_{min,i} \quad \forall i$$

3. Shipping time limit:
   $$t_i \leq t_{max} \quad \forall i$$

4. Logical constraint:
   $$l_i \leq L_{total} y_i \quad \forall i$$

5. Non-negativity and binary constraints:
   $$p_i, l_i, t_i \geq 0 \quad \forall i$$
   $$y_i \in \{0,1\} \quad \forall i$$

## Output
1. Crops included in the proposal: $y_i = 1$
2. Prices offered to producers: $p_i$
3. Logistics allocated: $l_i$ and associated cost $c_l l_i$
4. Earliest shipping days: $t_i$
5. Total profit: $Z$