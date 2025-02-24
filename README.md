# JS QUEUE
```
class Queue {
    constructor() {
        this.elements = {};
        this.head = 0;
        this.tail = 0;
    }

    enqueue(element) {
        this.elements[this.tail] = element;
        this.tail++;
    }

    dequeue() {
        if (this.head === this.tail) {
            return undefined;
        }
        const item = this.elements[this.head];
        delete this.elements[this.head];
        this.head++;
        return item;
    }

    peek() {
        return this.elements[this.head];
    }

    get size() {
        return this.tail - this.head;
    }

    get isEmpty() {
        return this.length === 0;
    }
}
```

# JS PRIORITY QUEUE
```
class PriorityQueue {
    constructor(comparator = (a, b) => a - b) {
        this.heap = [];
        this.comparator = comparator;
    }

    size() {
        return this.heap.length;
    }

    isEmpty() {
        return this.size() === 0;
    }

    peek() {
        return this.heap[0];
    }

    enqueue(value) {
        this.heap.push(value);
        this.bubbleUp(this.size() - 1);
    }

    dequeue() {
        if (this.isEmpty()) {
            return null;
        }
        const top = this.peek();
        const last = this.heap.pop();
        if (this.size() > 0) {
            this.heap[0] = last;
            this.bubbleDown(0);
        }
        return top;
    }

    bubbleUp(index) {
        while (index > 0) {
            const parentIndex = Math.floor((index - 1) / 2);
            if (this.comparator(this.heap[index], this.heap[parentIndex]) < 0) {
                this.swap(index, parentIndex);
                index = parentIndex;
            } else {
                break;
            }
        }
    }

    bubbleDown(index) {
        while (true) {
            const leftChildIndex = 2 * index + 1;
            const rightChildIndex = 2 * index + 2;
            let extremeChildIndex = index;

            if (
                leftChildIndex < this.size() &&
                this.comparator(this.heap[leftChildIndex], this.heap[extremeChildIndex]) < 0
            ) {
                extremeChildIndex = leftChildIndex;
            }

            if (
                rightChildIndex < this.size() &&
                this.comparator(this.heap[rightChildIndex], this.heap[extremeChildIndex]) < 0
            ) {
                extremeChildIndex = rightChildIndex;
            }

            if (extremeChildIndex !== index) {
                this.swap(index, extremeChildIndex);
                index = extremeChildIndex;
            } else {
                break;
            }
        }
    }

    swap(i, j) {
        [this.heap[i], this.heap[j]] = [this.heap[j], this.heap[i]];
    }
}
```

# TS QUEUE
```
class Queue<T> {
    private elements: { [key: number]: T };
    private head: number;
    private tail: number;

    constructor() {
        this.elements = {};
        this.head = 0;
        this.tail = 0;
    }

    enqueue(element: T): void {
        this.elements[this.tail] = element;
        this.tail++;
    }

    dequeue(): T | undefined {
        if (this.head === this.tail) {
            return undefined;
        }
        const item = this.elements[this.head];
        delete this.elements[this.head];
        this.head++;
        return item;
    }

    peek(): T | undefined {
        return this.elements[this.head];
    }

    get size(): number {
        return this.tail - this.head;
    }

    get isEmpty(): boolean {
        return this.size === 0;
    }
}
```

# TS PRIORITY QUEUE
```
class PriorityQueue<T> {
    private heap: T[];
    private comparator: (a: T, b: T) => number;

    constructor(comparator: (a: T, b: T) => number = (a, b) => {
        if (typeof a === 'number' && typeof b === 'number') {
            return a - b;
        } else {
            throw new Error("Default comparator only works for numbers. Please provide a custom comparator for other types.");
        }
    }) {
        this.heap = [];
        this.comparator = comparator;
    }

    size(): number {
        return this.heap.length;
    }

    isEmpty(): boolean {
        return this.size() === 0;
    }

    peek(): T | undefined {
        return this.heap[0];
    }

    enqueue(value: T): void {
        this.heap.push(value);
        this.bubbleUp(this.size() - 1);
    }

    dequeue(): T | undefined {
        if (this.isEmpty()) {
            return undefined;
        }
        const top = this.peek();
        const last = this.heap.pop();
        if (this.size() > 0) {
            this.heap[0] = last;
            this.bubbleDown(0);
        }
        return top;
    }

    private bubbleUp(index: number): void {
        while (index > 0) {
            const parentIndex = Math.floor((index - 1) / 2);
            if (this.comparator(this.heap[index], this.heap[parentIndex]) < 0) {
                this.swap(index, parentIndex);
                index = parentIndex;
            } else {
                break;
            }
        }
    }

    private bubbleDown(index: number): void {
        while (true) {
            const leftChildIndex = 2 * index + 1;
            const rightChildIndex = 2 * index + 2;
            let extremeChildIndex = index;

            if (
                leftChildIndex < this.size() &&
                this.comparator(this.heap[leftChildIndex], this.heap[extremeChildIndex]) < 0
            ) {
                extremeChildIndex = leftChildIndex;
            }

            if (
                rightChildIndex < this.size() &&
                this.comparator(this.heap[rightChildIndex], this.heap[extremeChildIndex]) < 0
            ) {
                extremeChildIndex = rightChildIndex;
            }

            if (extremeChildIndex !== index) {
                this.swap(index, extremeChildIndex);
                index = extremeChildIndex;
            } else {
                break;
            }
        }
    }

    private swap(i: number, j: number): void {
        [this.heap[i], this.heap[j]] = [this.heap[j], this.heap[i]];
    }
}
```
