As a user with a To-Do list I want to be able to: 
- Add items to a list to remind the user of what they need to do. 
- Remove items as you complete them. 
- switch between views of All items, Active items, Completed Items.

Output box. If user inputs data and hits enter or clicks a add button then add data to list.

List of items If user has input data and it has been added to the list then options of Completing and deleting task becomes available. If user completes task on item, and completed button is used, item is then taken to the completed state. then if its in the completed section you have the option of removing your item with a delete button. Be able to use local storage to store items in it

Buttons to navigate Use buttons to pull in the different states for Completed, Active, All items.

## Model View Controller (MVC)

### Model (stores data)
    store form input value by user as a to-do item in state
    store whether todo has been completed/deleted
    store amount of todo items added
### View (renders display)
    show todos filtered by completed or not
    show todo crossed out/checked off when completed
    show count of number of todo items left
    show remove button for each todo item
### Controller (handles input)
    handle click events for adding, deleting and completing a todo item
    handle click event for different filters for the displayed todo items


### 

    const completeTask = (e) => {
        let index = itemList.findIndex(x => x.id === parseInt(e.target.dataset.id));
        itemList[index].status = 'complete';
        localStorage.setItem('list', JSON.stringify(itemList));
     const deleteTask = (e) => {
          let store = JSON.parse(localStorage.getItem("itemsArray")) || [];
        for (let i = 0; i < store.length; i++) {
            store.splice(i, 1);
            localStorage.setItem('itemsArray', JSON.stringify(store));
    
    What does everything do?
    header
        doesn't change
    input field
        loads default text when no text entered
        can be clicked
        can have text entered
        submit button
            can be clicked
            adds entered text to list when clicked if unique
    list
        takes in list items
        loses list items
        list items
            can be clicked
            can be checked
            can be removed
    bottom bar
        number of items
            updates when list changes
        all + active + completed
            can be clicked
            changes list

Program
    'todos' heading
    'What needs to be done?' input field
        Type something in, hit enter or button to add to list
        New list item added to active
        What if what you entered is not unique or blank?
    List
        List items
            Have text
            A 'O' for a checkmark
                Crosses text on click
                Adds list item to completed
            An 'X' on hover
                Removes list item on click
    Bottom bar
        Active items counter
        All + Active + completed
            Filters list accordingly when clicked
            Boxed when last clicked
            Transparent box on hover
        Clear completed button
            Loads when list items have been added to completed
            Hides after clicked or when no completed items

What is in the interface?
    heading
    Input field
        Enter button
        Default text
        Text input
    List
        List items
            Text
            Checkmark circle
            X when hovered
    Bottom bar
        Active items counter
        Filter options
            All
            Active
            Completed



What objects are there?
    Heading
    Input Bar
        Submit Button
        Input Field
    List
        List Items
            Check Circle
            Text
            X
    Filter Bar
        Active Counter
        Filters
            All
            Active
            Completed
        Clear Button

What can the user do?
    typeText()
    hitSubmitButton()
    checkListItem()
    removeListItem()
    chooseAll()
    chooseActive()
    chooseCompleted()
    hitClearButton()

What does the system do?
    displaysHeading()
    displaysInputBar()
    displaysDefaultText()
    displaysTypedText()
    if list items > 0
        displaysList()
        displaysFilterBar()
    addsListItemToActive()
    makeListItemCompleted()
    deletesListItem()
    updatesCounter()
    filtersList()
    clearsCompleted()

Follow 'Thinking in React' to turn into React pseudocode

What data do we need to load any instance of the program?
    What is in the input field 
    What list items are in the list
    Which filter is chosen

List = {
    typed: "",
    filter: "",
    items: []
}

Item = {
    text: "", 
    done: true/false
}

App
    Data to Render
        Entered Text
        List Items
            ID
            Text
            Status
        Selected Filter
    User Stories
        submitClicked() -> addListItem()
        checkClicked() -> checkItem()
        removeClicked() -> removeItem()
        filterClicked() -> changeFilter()
        clearClicked() -> clearCompleted()
    System
        render() -> InputBar
                    List
                    FilterBar

addClicked
    // add list item to list
    create list item
    item.text = input