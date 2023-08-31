# NotesWall
NotesWall is a simple note taking app that allows users to create and save notes. 
# Hosted Link:
https://ronaksharma57.github.io/NotesWall/

## Prerequisites

To run NotesWall, you will need the following:

* Node.js installed on your system.
* A text editor or IDE.

## Installation

To install NotesWall, clone the repository and install the dependencies:

```
git clone https://github.com/Day12Classroom/NotesWall.git
cd NotesWall
npm install
```

## Usage

To start NotesWall, run the following command:

```
npm start
```

This will start the app on port 3000. You can then access the app by visiting http://localhost:3000 in your browser.

## Features

NotesWall has the following features:

* Create notes: Users can create notes by typing text into the input field and clicking the "Add note" button.
* Save notes: Notes are automatically saved to the browser's local storage.
* Delete notes: Users can delete notes by clicking the "X" button on the note.
* Change note color: Users can change the color of a note by clicking on the color picker and selecting a new color.

## Code Explanation

The code for NotesWall is relatively simple. The main file is index.js. This file contains the following code:
# js
```

const input = document.querySelector('.get-note');
const addNoteBtn = document.querySelector('#add-btn');
addNoteBtn.addEventListener("click", addNewNote);
const allNotes = [];

const color = document.querySelector('.get-color');
const notesList = document.querySelector('.notes-list');

document.addEventListener('keypress', (event) => {
    if (event.keyCode === 13) {
        addNewNote();
    }
})

function addNewNote() {
    if (input.value) {
        let newNote = {
            note: input.value,
            noteColor: color.value

        };
        allNotes.push(newNote);
    }
    else {
        alert("A note can't be empty.");

    }
   



    input.value = "";
    input.focus();
    
    displayNotes(allNotes);

    
   
}


function displayNotes(notes) {
    notesList.innerHTML = " ";
    notes.forEach(element => {
       let noteHTML= `
        <div class="note" style="background-color:${element.noteColor};">
            <div class="note-view">
                ${element.note}
            </div>
            <div>
                <a class="deleteBtn">Del</a>
            </div>
        </div>
        `;

        notesList.insertAdjacentHTML('afterbegin', noteHTML);
        
        const deleteBtn = document.querySelector('.deleteBtn');
        deleteBtn.addEventListener('click', e => { deleteNote(e,element);})


    });
}


function deleteNote(e,element) {
    let item = e.target.parentElement.parentElement.parentElement;
    item.parentNode.removeChild(item);
    allNotes.pop(element);
    
}
```

