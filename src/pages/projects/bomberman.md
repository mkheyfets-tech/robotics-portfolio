---
layout: ../../layouts/Layout.astro
title: Bomberman Escape AI
summary: Autonomous Python agents that combine A* and minimax search for navigation with reinforcement learning for bomb placement and hazard avoidance.
image: /robotics-portfolio/bomberman.svg
tech: [Python, A* Search, Minimax, Reinforcement Learning]
order: -1
---

# Bomberman Escape AI

<img
  src="/robotics-portfolio/bomberman.svg"
  alt="Project 2, Variant 2 map with the original game sprites, four wall barriers, a random monster, and the exit."
  width="1006"
  height="910"
  style="width: 100%; height: auto; border-radius: 12px; border: 1px solid var(--border-color); margin: 1.5rem 0;"
/>

### Project Overview

I explored autonomous decision-making through two Python agents built on a shared Bomberman game engine. Both agents navigate from the top-left corner of a grid to an exit while responding to moving monsters. The second agent also uses bombs to destroy walls that block its route.

The project connects two approaches to the same navigation problem: planning with search algorithms and learning a state evaluation from experience. It provides a compact environment for exploring how an agent balances progress toward a goal with the need to avoid hazards.

### Hybrid Path Planning

The first agent combines **A* pathfinding** with **minimax search**. It follows an A* route when the exit is reachable and monsters are far away. When a monster comes within four cells by Euclidean distance, or no path is available, the agent switches to a minimax search with a depth of two to select its next move.

Standalone A* and minimax agents provide alternative strategies to compare against the hybrid approach. Decision-time logging and a final move count help examine the computational cost and movement behavior of each run.

### Learning to Use Bombs

The second agent evaluates movement, waiting, and bomb-placement actions by simulating their next states. It scores each action using an immediate custom reward plus a discounted estimate of the resulting state's value, then updates its feature weights during play.

Its six state features describe proximity to monsters, the exit, and explosions; exposure to a bomb's blast radius; whether a monster is in chasing range; and monster proximity measured with Chebyshev distance to account for diagonal movement.

The learning rate is **0.05**, and the discount factor is **0.9**. An optional weight-saving mechanism supports continued learning across episodes, while a separate agent uses loaded weights without updating them during play.

### Scenario Design

Both approaches run across five scenarios with increasing environmental complexity:

- **No monsters:** Navigate the map and reach the exit.
- **Random monster:** React to an opponent that chooses among reachable cells at random.
- **Self-preserving monster:** Avoid an opponent that accounts for explosions when changing direction and attacks nearby agents.
- **Aggressive monster:** Respond to an opponent with a larger detection range.
- **Mixed opponents:** Navigate around random and aggressive monsters in the same map.

The bomb-navigation scenarios add destructible walls, requiring the agent to create a route while accounting for blast hazards. The implementation includes alternate agents, saved weights, and additional maps for experimentation.

### Source Code

Explore the agent implementations, scenario scripts, and setup instructions in the repository.

<a href="https://github.com/mkheyfets-tech/Bomberman_Escape_AI.git" target="_blank" rel="noopener noreferrer" class="btn-report">
  <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" aria-hidden="true"><path d="m8 8-4 4 4 4M16 8l4 4-4 4M14 4l-4 16"></path></svg>
  View Source on GitHub
</a>
