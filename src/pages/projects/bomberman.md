---
layout: ../../layouts/Layout.astro
title: "Bomberman Escape AI"
summary: "Python agents that find a way out of Bomberman using path planning, adversarial search, and reinforcement learning."
discipline: "Autonomous planning & AI"
context: "Personal project · Python simulation"
order: -1
imageClass: "game"
image: /robotics-portfolio/bomberman.svg
tech: ["Python", "A* Search", "Minimax", "Reinforcement Learning"]
---

<figure class="game-figure">
  <img src="/robotics-portfolio/bomberman.svg" width="1006" height="910" alt="Original Bomberman map with four wall barriers, a player at the top left, a monster, and an exit at the bottom right." />
  <figcaption>Project 2, Variant 2: the agent must clear four wall barriers to reach the exit.</figcaption>
</figure>

## The problem

Getting to the exit is straightforward until the route is blocked or a monster gets in the way. I used Bomberman to explore how an agent can make progress toward a goal while responding to a changing environment.

The project contains two approaches built on a shared game engine: a search-based agent for navigation and a learning agent that also places bombs to clear walls.

## Planning a route—and knowing when to change it

The first agent follows an **A\* path** when the exit is reachable and monsters are far away. When a monster comes within four cells by Euclidean distance, or no route is available, it switches to a **depth-two minimax search** to choose its next move.

Standalone A* and minimax agents make it possible to compare the strategies. The hybrid agent logs decision times and its final move count so each run can be examined beyond simply reaching the exit.

## Learning to clear obstacles

The second agent simulates movement, waiting, and bomb-placement actions. It combines an immediate reward with a discounted estimate of the next state's value, then updates its feature weights during play.

Six features describe the exit, nearby monsters and explosions, blast exposure, and whether a monster is in chasing range. The agent uses a learning rate of **0.05** and a discount factor of **0.9**. Weight saving is optional, and a separate agent can use saved weights without updating them.

## Putting the agents through different scenarios

Both approaches run in five environments: no monsters, a random monster, a self-preserving monster, an aggressive monster, and a mix of random and aggressive opponents. The second project's map adds destructible walls, making bomb placement and blast avoidance part of the navigation problem.

The repository includes the agents, scenario scripts, maps, and setup instructions.

<a href="https://github.com/mkheyfets-tech/Bomberman_Escape_AI.git" target="_blank" rel="noopener noreferrer" class="btn-report">View source on GitHub <span aria-hidden="true">↗</span></a>
