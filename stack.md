# Implementasi Sederhana Stack dengan Java

```
class Stack {
	private final int MAX_N = 100;

	private int top;
	private int stack[] = new int[MAX_N];

	public void init() {
		top = 0;
	}

	public boolean isEmpty() {
		return (top == 0);
	}

	public boolean isFull() {
		return (top == MAX_N);
	}

	public boolean push(int value) {
		if (isFull()) {

			System.out.println("stack overflow!");
			return false;
		}
		stack[top] = value;
		top++;

		return true;
	}

	public Integer pop() {
		if (top == 0) {
			System.out.println("stack is empty!");
			return null;
		}

		top--;
		Integer value = new Integer(stack[top]);

		return value;
	}
}
```
