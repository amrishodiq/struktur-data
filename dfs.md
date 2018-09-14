# Implementasi algoritma DFS dengan Java


```
class DFS {
	final int MAX_VERTEX = 30;
	int[][] map = new int[MAX_VERTEX][MAX_VERTEX];
	boolean[] visit = new boolean[MAX_VERTEX];
	int vertex;
	int edge;
	int maxEdge;
	int start;
	int end;

	public void setVertex(int vertex) {
		this.vertex = vertex;
	}

	public void setEdge(int edge) {
		this.edge = edge;
	}

	public void setMaxEdge(int maxEdge) {
		this.maxEdge = maxEdge;
	}
	
	public int getMaxEdge() {
		return this.maxEdge;
	}

	public void setStart(int start) {
		this.start = start;
	}

	public void setEnd(int end) {
		this.end = end;
	}
	
	public void setConnected(int v1, int v2) {
		map[v1][v2] = 1;
	}

	public void start(int v, int depth) {
		// awasi kapan harus berhenti karena ini recursive.
		if (v == end) {
			if (maxEdge < 0 || depth < maxEdge) {
				maxEdge = depth;
			}
			return;
		}
		
		visit[v] = true;
		for (int i = 1; i <= vertex; i++) {
			if (map[v][i] == 1 && !visit[i]) {
				start(i, depth + 1);
				visit[i] = false;
			}
		}
	}
	
	public void printConnections() {
		for (int i=0; i<MAX_VERTEX; i++) {
			for (int j=0; j<MAX_VERTEX; j++) {
				System.out.print(map[i][j]+" ");
			}
			System.out.println();
		}
	}
}

public class Solution {

	public static void main(String[] args) {
		DFS dfs = new DFS();
		dfs.setVertex(8);
		dfs.setEdge(10);
		dfs.setStart(1);
		dfs.setEnd(8);
		dfs.setMaxEdge(-1);
		
		dfs.setConnected(1, 2);
		dfs.setConnected(1, 3);
		dfs.setConnected(2, 7);
		dfs.setConnected(2, 4);
		dfs.setConnected(3, 5);
		dfs.setConnected(3, 6);
		dfs.setConnected(4, 7);
		dfs.setConnected(5, 7);
		dfs.setConnected(6, 7);
		dfs.setConnected(6, 8);
		
		dfs.printConnections();
		
		dfs.start(1, 0);
	}

}
```
