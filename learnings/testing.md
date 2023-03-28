# Testing portfolio

### TuDo - a personal productivity app for managing tasks

![image](https://user-images.githubusercontent.com/32879360/228196408-e094a5a9-320d-4148-9b29-98cea245af81.png)

## 1. Check that passing a given input into our tests returns the expected output

The testing library that we developed for this project was centred around the following functions which check that output is expected:

```javascript
function isEqual(expected, output, message = `you expected ${expected} and got ${output}`){
    if (expected === output) {
        console.info(`%cPASS: ${message}`, 'color:green; font-size:12px');
    }else{
        console.info(`%cFAIl: ${message}`, "color:darkred; font-size:12px");
    }
};

function isDifferent(expected, output, message = `you expected ${expected} and got ${output}`){
    if (expected !== output){
        console.info(`%cPASS: ${message}`, "color:green; font-size:12px");
    }else{
        console.info(`%cFAIL: ${message}`, 'color:darkred; font-size:12px');
    }
}
```

## 2. Write tests to mimic the behaviour of a user performing different actions

We end-to-end tested all of the major functionality of the web app by mimicking user interaction. Here is an example of one of the user interaction tests:

```javascript
function typeToCreate() {
    let expected = 'test task';

    let emptyTask = document.querySelectorAll('.item__description')[0];
    emptyTask.value = 'test task';
    emptyTask.dispatchEvent(pressEnter);
    
    let testInput = document.querySelectorAll('.item__description')[1];
    testInput.classList.add('test-task');

    taskCollection.getAllTasksFromStorage();
    let output = testInput.value;
    
    isEqual(expected, output, 'created a test task');
};
```
These tests were bundled into a function runTests() that would run them automatically at key points in the development cycle:

```javascript
function runTests(){
    let allStrings = [
        'typing a new task adds it to the stored list', 
        'editing an existing item will change the associated task',
        'typing "/done" marks a task as completed', 
        'typing "/pending" marks a task as pending',
        'typing "/delete" removes a task', 
        'the number of tasks displayed matches the number of task objects in storage'
    ];

    let allTests = [
        typeToCreate, 
        typeToEdit,
        typeToComplete, 
        typeToUncheck,
        typeToDelete, 
        trackTaskListInStorage
    ];
    
    for(let i = 0; i < allTests.length; i++){
        setTimeout(() => test(allStrings[i], allTests[i]), i * 1000);
    }
}
```

## 3. Write testable, modular functions

The app was designed from the beginning to be modular and testable. Two main JS classes stored state and logic for the 'tasks'. These were instantiated in the main app entry point and their methods called in response to user input or testing. Here is an example TaskCollection class and sample methods:

```javascript
export class TaskCollection {
  constructor() {
    this.allTasks = [];
  }

  addTask(task) {
    this.allTasks.push(task);
    this.saveAllTasksToStorage();
  }

  deleteTask(index) {
    this.allTasks.splice(index, 1);
    this.saveAllTasksToStorage();
  }

  editTask(index, newDescription, newStatus) {
    let currentTask = this.allTasks[index];
    currentTask.description = newDescription;
    currentTask.status = newStatus;

    this.saveAllTasksToStorage();
  }
```

## 4. Write functions that add, remove or modify DOM nodes

DOM manipulation was a mainstay of this project. It was used to display tasks and control how they are styled. As an example, the following function allows the user to toggle between a light and dark theme which is controlled by a 'data-theme' HTML attribute on the root element:

```javascript
function toggleTheme(event) {
  const element = event.srcElement;
  const bodyElement = document.querySelector("body");

  const currentTheme = bodyElement.getAttribute("data-theme");

  if (currentTheme === "light") {
    element.innerHTML = "&#9728";
    bodyElement.setAttribute("data-theme", "dark");
  } else {
    element.innerHTML = "&#9790";
    bodyElement.setAttribute("data-theme", "light");
  }
}
```

## 5. Apply event listeners to HTML form elements



## 6. Use scope to control what variables are accessible inside functions and blocks



## 7. Use CSS grid to create complex layouts



## 8. Use CSS grid to make layouts that adapt to the viewport size

