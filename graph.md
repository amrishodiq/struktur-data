# Implementasi sederhana Graph dengan Java


```
class Graph {

	class Node {
		int vertex;
		Node next;

		public Node(int v) {
			vertex = v;
			next = null;
		}
	}

	class List {
		int count;
		Node head;
		Node tail;

		public List() {
			count = 0;
			head = tail = null;
		}
	}

	int numberOfVertices;
	List[] list;

	public Graph(int n) {
		numberOfVertices = n;
		list = new List[n];
		for (int i = 0; i < n; i++) {
			list[i] = new List();
		}
	}

	void addEdge(int src, int dest) {
		Node newNode = new Node(dest);
		if (list[src].tail != null) {
			list[src].tail.next = newNode;
			list[src].tail = newNode;
		} else {
			list[src].head = list[src].tail = newNode;
		}
		list[src].count++;

		newNode = new Node(src);
		if (list[dest].tail != null) {
			list[dest].tail.next = newNode;
			list[dest].tail = newNode;
		} else {
			list[dest].head = list[dest].tail = newNode;
		}
		list[dest].count++;
	}

	void display(int i) {
		Node current = list[i].head;
		while (current != null) {
			System.out.printf("%d ", current.vertex);
			current = current.next;
		}
		System.out.printf("\n");
	}
}
```
