---
title: "Sudoku Solution Validator"
date: 2018-07-16T21:32:16+08:00
tags: [
    "go",
    "golang",
    "sudoku",
    "算法",
    "数独",
]
categories: [
    "算法",
]
---

```go
func ValidateSolution(m [][]int) bool {
	for outer_idx, outer_val := range m {
		var row, col, grid [10]bool
		for inner_idx, inner_val := range outer_val {
			// validate row
			if inner_val == 0 || row[inner_val] == true {
				return false
			} else {
				row[inner_val] = true
			}

			// validate column
			key := m[inner_idx][outer_idx]
			if col[key] == true {
				return false
			} else {
				col[key] = true
			}

			// validate grid
			x := 3*(outer_idx/3) + inner_idx/3
			y := 3*(outer_idx%3) + inner_idx%3
			key = m[x][y]
			if grid[key] == true {
				return false
			} else {
				grid[key] = true
			}
		}
	}

	return true
}
```