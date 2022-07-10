class Node {
  constructor(element) {
    this.element = element;
    this.next = null;
  }
}

class LinkedList {
  constructor() {
    this.head = null;
    this.size = 0;
  }

  add(element) {
    var node = new Node(element);

    var curr;
    if (this.head == null) {
      this.head = node;
    } else {
      curr = this.head;
      while (curr.next) {
        curr = curr.next;
      }
      curr.next = node;
    }
    this.size++;
  }

  addAfterIndex(element, index) {
    if (this.size < index || index < 0) {
      return console.log("Enter valid index");
    } else {
      var node = new Node(element);
      let curr;
      let prv;
      if (index == 0) {
        node.next = this.head;
        this.head = node;
      } else {
        curr = this.head;
        let i = 0;
        while (i < index) {
          i++;
          prv = curr;
          curr = curr.next;
        }
        node.next = curr;
        prv.next = node;
      }
      this.size++;
    }
  }

  removeAfterIndex(index) {
    if (index < 0 || index > this.head) {
      return console.log("Enter valid input");
    } else {
      let curr = this.head;
      let prv = curr;
      if (index == 0) {
        this.head = curr.next;
      } else {
        let i = 0;
        while (i < index) {
          i++;
          prv = curr;
          curr = curr.next;
        }
        prv.next = curr.next;
      }
    }
    this.size--;
  }

  printList() {
    let curr = this.head;
    let str = "";
    while (curr) {
      str += curr.element;
      curr = curr.next;
    }
    console.log(str);
  }
}
var ll = new LinkedList();
ll.add(10);
ll.add(20);
ll.add(30);
ll.printList();
ll.addAfterIndex(40, 1);
ll.printList();
ll.removeAfterIndex(2);
ll.printList();
