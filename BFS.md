基础版本，不分level
```
private void bfs(boolean[][] grid, Point p) {
    Queue<Point> queue = new LinkedList<Point>();
    int[] dircX = {1, -1, 0, 0};
    int[] dircY = {0, 0, -1, 1};
    queue.offer(p);
    while (!queue.isEmpty()) {
        Point temp = queue.poll();
        grid[temp.x][temp.y] = false;
        for (int i = 0; i <4; i++) {
            Point adj = new Point(temp.x + dircX[i], temp.y + dircY[i]);
            if (isValid(adj) && grid[adj.x][adj.y] == true) {
                queue.offer(adj);
            }
        }
    }
}
```
