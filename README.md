#QUEUE
```
class Queue<T> {
    private elements: { [key: number]: T } = {};
    private head: number = 0;
    private tail: number = 0;

    enqueue(element: T): void {
        this.elements[this.tail] = element;
        this.tail++;
    }

    dequeue(): T | undefined {
        if (this.head === this.tail) return undefined;
        const item = this.elements[this.head];
        delete this.elements[this.head];
        this.head++;
        return item;
    }

    peek(): T | undefined {
        return this.elements[this.head];
    }

    get length(): number {
        return this.tail - this.head;
    }

    get isEmpty(): boolean {
        return this.length === 0;
    }
}
```

#STACK
```
class Stack {
    constructor() { 
        this.items = []; 
    }

    push(element) { 
	    this.items.push(element);
    }

    pop() { 
        if (this.items.length == 0) 
            return "Underflow"; 
        return this.items.pop(); 
    }
    
    isEmpty() { 
        return this.items.length == 0; 
    }

    peek() { 
        return this.items[this.items.length - 1]; 
    } 
}
```
