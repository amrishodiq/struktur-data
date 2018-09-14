# Implementasi Sederhana LinkedList dengan Java


```
class LinkedList<T> {
	public class Node {
		T data;
		public Node next;
		public Node(T data) {
			this.data = data;
		}
	}
	
	private Node head;
	private Node tail;
	
	public LinkedList() {
	}
	
	public void add(T data) {
		if (head == null) {
			head = new Node(data);
			tail = head;
		} else {
			tail.next = new Node(data);
			tail = tail.next;
		}
	}
	
	public void delete(T data) {
		Node current = head;
		if (current.data.equals(data)) {
			if (head.next != null) {
				head = head.next;
			} else {
				head = null;
				tail = null;
			}
		}
		
		while (current.next != null) {
			Node previous = current;
			current = current.next;
			if (current.data.equals(data)) {
				System.out.println("Delete "+current.data);
				previous.next = current.next;
			}
		}
	}
	
	public void printAll() {
		Node current = head;
		System.out.println(current.data);
		
		while (current.next != null) {
			current = current.next;
			System.out.println(current.data);
		}
	}
}
```
