# Triangle Light Maze Solver

An interactive visualization of dynamic programming. Build a triangular maze, mark its glowing nodes, and find a path from the top to the bottom that collects the most lights.

**[Open the live demo](https://lamplighter-commons.github.io/triangle-light-maze-solver/)** · [中文说明](README.zh-CN.md) · [Report an issue](https://github.com/lamplighter-commons/triangle-light-maze-solver/issues)

Runs entirely in your browser. No installation, dependencies, or build step. The application interface is currently in Chinese.

## Preview

| Maze editor | Solved example |
| --- | --- |
| ![Triangle maze editor](assets/screenshot-home.png) | ![Solved maze with its optimal path highlighted](assets/screenshot-demo.png) |

## Features

- Create and edit triangular mazes with 1–30 rows.
- Toggle glowing nodes with mouse or keyboard controls.
- Visualize the optimal path and inspect the dynamic programming table.
- Choose left or right preference when paths have the same score.
- See the score, captured lights, capture rate, and algorithm complexity.
- Load an example, clear the lights, or reset the maze.
- Download the project and use it offline.

## Try it

1. Enter the number of rows and select **生成迷阵** (Generate maze).
2. Select nodes to mark them as glowing.
3. Choose a tie-breaking preference.
4. Select **运行求解** (Run solver) to see the result.

For a quick example, select **查看示例解** (Show example solution). **清空发光点** clears the lights while preserving the maze; **完全重置** resets the maze and results.

## Run locally

Download or clone the repository, then open `index.html` in your browser. You can also serve the directory locally:

```bash
python3 -m http.server 8000
```

Open `http://localhost:8000`.

## How it works

The solver uses dynamic programming followed by path reconstruction:

- `dp[r][c]` stores the maximum number of glowing nodes collected on a path from the top to node `(r, c)`.
- `parent[r][c]` records the selected parent in the previous row.
- The best endpoint in the last row is selected, then the path is reconstructed through the parent entries.

For equal scores, `preferLeft` selects the left parent or endpoint; `preferRight` selects the right one. Time and space complexity are both **O(n²)**.

## Development checks

Run these from the repository root with Node.js installed:

```bash
node --test tests/solver.test.js
node scripts/smoke-test.js
node scripts/check-release.js
```

The first command checks the solver, the second runs a smoke check, and the third checks release assets and documentation references.

## Contributing

Bug reports, clearer explanations, accessibility improvements, and code contributions are welcome. See the [contribution guide](https://github.com/lamplighter-commons/.github/blob/main/CONTRIBUTING.md). Issues and pull requests may be written in English or Chinese.

If you find this project useful, consider starring it, sharing it, or contributing.

## License

[MIT](LICENSE). Maintained by [Lamplighter Commons](https://github.com/lamplighter-commons), started by [Jingming Liang](https://github.com/eprogressing).
