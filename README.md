<!DOCTYPE html>
<html>
<head>
    <title>My Simple Organizer</title>
     <link rel="icon" type="image/png" href="https://cdn-icons-png.freepik.com/512/14385/14385612.png">
    <style>
        :root {
            --primary-color: #6c5ce7;
            --secondary-color: #a8a5e6;
            --success-color: #00b894;
            --danger-color: #d63031;
            --text-color: #2d3436;
            --bg-color: rgba(255, 255, 255, 0.9);
        }

        body {
            font-family: 'Segoe UI', system-ui, sans-serif;
            margin: 0;
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            background: linear-gradient(135deg, #f0f2f5 0%, #dfe6e9 100%);
            transition: background-color 0.3s ease, color 0.3s ease;
        }

       .background-media {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    object-fit: cover;
    z-index: -1;
    opacity: 0.4;
    transition: opacity 0.3s ease;
}

#background-video {
    display: none;
}
#background-image {
    display: none;
}

#background-video.active,
#background-image.active {
    display: block;
}
        #container {
            position: relative;
            display: flex;
            flex-direction: column;
            width: 100%;
            max-width: 800px;
            background: transparent !important;
            backdrop-filter: none !important;
            box-shadow: none !important;
            padding: 2rem;
            border-radius: 0px;
            backdrop-filter: blur(0px);
            margin: 0rem;
            z-index: 1;
        }

        #header {
            display: flex;
            align-items: center;
            justify-content: space-between;
            margin-bottom: 1.5rem;
            padding-bottom: 1rem;
            border-bottom: 2px solid rgba(0, 0, 0, 0.1);
        }

        #title {
            font-size: 1.8rem;
            font-weight: 600;
            color: var(--primary-color);
            margin: 0;
        }

        .controls-container {
            display: flex;
            align-items: center;
            gap: 1rem;
        }

        #add-button {
            padding: 0.6rem 1.2rem;
            background-color: var(--primary-color);
            color: white;
            border: none;
            border-radius: 8px;
            cursor: pointer;
            transition: all 0.2s ease;
            display: flex;
            align-items: center;
            gap: 0.5rem;
        }

        #add-button:hover {
            background-color: #5b4bc4;
            transform: translateY(-1px);
        }
#add-button,  /* Add this to your CSS */
.menu-button {   /* Add this to your CSS */
    -webkit-user-select: none; /* Safari */
    -moz-user-select: none; /* Firefox */
    -ms-user-select: none; /* Internet Explorer/Edge */
    user-select: none; /* Standard syntax */
}

        .icon-button {
            width: 40px;
            height: 40px;
            border-radius: 50%;
            background: rgba(0, 0, 0, 0.05);
            border: none;
            cursor: pointer;
            transition: all 0.2s ease;
            display: grid;
            place-items: center;
        }

        .icon-button:hover {
            background: rgba(0, 0, 0, 0.1);
        }

        .note {
            display: flex;
            align-items: flex-start;
            gap: 1rem;
            padding: 1rem;
            margin-bottom: 1rem;
            border-radius: 12px;
            background: white;
            box-shadow: 0 2px 8px rgba(0, 0, 0, 0.05);
            transition: all 0.2s ease;
            cursor: grab; /* Change cursor on note hover */
    transition: transform 0.2s ease; /* Add transition for smooth dragging effect */
}
.note {
    user-select: none; /* Prevents text selection within the entire note */
    /* ... other styles ... */
}

/* Or, if you only want to prevent selection in certain parts of the note: */
.note-content {
    user-select: none; /* Prevents text selection only within the content area */
}
   .note {
    -webkit-user-select: none; /* Safari */
    -moz-user-select: none; /* Firefox */
    -ms-user-select: none; /* Internet Explorer/Edge */
    user-select: none; /* Standard syntax */
}
      .note.dragging {
    box-shadow: 0 8px 20px rgba(0,0,0,0.2);
    opacity: 0.9;
    cursor: grabbing;
}

/* Add this to prevent content shift */
#notes-list {
    transition: transform 0.2s ease;
}
        .star-button {
    background: none;
    border: none;
    cursor: pointer;
    font-size: 1.2rem; /* Adjust star size as needed */
    color: gray; /* Initial star color */
    transition: color 0.2s ease;
    padding: 0;
    width: 32px;
    height: 32px;
    display: flex;
    align-items: center;
    justify-content: center;
}
           .star-button.active {
    color: gold; /* Star color when active */
}
.note.important {
    background-color: #ffebee; /* Light red background for important tasks */
}
body.dark-mode .note.important{
    background-color: #59323c;
}
      
           .note:hover {
            transform: translateX(4px);
            box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
        }

        .note-content {
            flex-grow: 1;
            margin-right: auto;
            padding: 0.5rem 0;
        }

        .edit-input {
            width: 100%;
            padding: 0.5rem;
            border: 1px solid var(--secondary-color);
            border-radius: 6px;
            font-family: inherit;
            font-size: inherit;
            background: transparent;
            color: inherit;
        }

        .note-actions {
            display: flex;
            gap: 0.5rem;
align-items: center; /* Vertically align items */
        }

        .note-button {
            padding: 0; /* Remove padding */
            border: none;
            border-radius: 50%; /* Make it circular */
            cursor: pointer;
            transition: all 0.2s ease;
            width: 32px;
            height: 32px;
            display: flex;
            align-items: center;
            justify-content: center;
            background: transparent; /* Make background transparent */
        }
        .edit-input {
            width: 100%;
            padding: 0.5rem;
            border: 1px solid var(--secondary-color);
            border-radius: 6px;
            font-family: inherit;
            font-size: inherit;
            background: transparent;
            color: inherit;
        }
        .note{
          display: flex;
        }
        .note-content{
          flex-grow: 1;
        }
        .edit-button{
          display:none;
        }
        
        .delete-button {
            background-color: transparent; /* Remove background color */
            color: var(--danger-color); /* Use danger color for icon */
            font-size: 1.2rem; /* Adjust icon size as needed */
        }
        .delete-button:hover{
          color: #ff4757;
        }

        .complete-checkbox {
            margin-top: 0.4rem;
            accent-color: var(--success-color);
        }

        .completed .note-content {
            text-decoration: line-through;
            opacity: 0.7;
        }

        /* Dark Mode Styles */
        body.dark-mode {
            background: #121212;
            color: #ffffff;
            --text-color: #ffffff;
            --bg-color: rgba(40, 40, 40, 0.9);
            --primary-color: #8477e6;
            --secondary-color: #6b63b3;
        }

        body.dark-mode #container {
            box-shadow: 0 8px 32px rgba(255, 255, 255, 0.05);
        }

        body.dark-mode .note {
            background: transparent;
        }

        body.dark-mode #header {
            border-bottom-color: rgba(255, 255, 255, 0.1);
        }

        body.dark-mode .icon-button {
            background: rgba(255, 255, 255, 0.1);
        }

        body.dark-mode .icon-button:hover {
            background: rgba(255, 255, 255, 0.2);
        }

        #search-container {
            display: flex;
            justify-content: center;
            margin-bottom: 2rem;
        }
#title span { /* Targets the span elements within #title */
    -webkit-user-select: none;
    -moz-user-select: none;
    -ms-user-select: none;
    user-select: none;
}

        #google-search-bar {
            width: 50%;
            max-width: 600px;
            padding: 1rem;
            padding-left: 3rem;
            border: none;
            border-radius: 30px;
            font-size: 1rem;
            box-shadow: 0 2px 5px rgba(0, 0, 0, 0.15);
            background-color: white;
            color: #333;
            transition: box-shadow 0.2s ease;
            outline: none;
            background-image: url("https://www.svgrepo.com/show/380993/google-logo-search-new.svg");
            background-repeat: no-repeat;
            background-position: 1rem center;
            background-size: 1.2rem 1.2rem;
        }
#google-search-bar::placeholder {
    -webkit-user-select: none; /* Safari */
    -moz-user-select: none; /* Firefox */
    -ms-user-select: none; /* Internet Explorer/Edge */
    user-select: none; /* Standard syntax */
}

        #google-search-bar:focus {
            box-shadow: 0 4px 10px rgba(0, 0, 0, 0.2);
        }

        #google-search-bar::placeholder {
            color: #999;
        }

        /* Dark Mode Styles for Search Bar */
        body.dark-mode #google-search-bar {
            background-color: #333;
            color: #eee;
            box-shadow: 0 2px 5px rgba(255, 255, 255, 0.1);
        }

        body.dark-mode #google-search-bar:focus {
            box-shadow: 0 4px 10px rgba(255, 255, 255, 0.2);
        }

        /* Modern Dropdown Menu Styles */
        .menu-button {
            width: 40px;
            height: 40px;
            border-radius: 50%;
            background: rgba(0, 0, 0, 0.05);
            border: none;
            cursor: pointer;
            transition: all 0.2s ease;
            display: grid;
            place-items: center;
            position: relative;
        }

        .menu-button:hover {
            background: rgba(0, 0, 0, 0.1);
        }

        .dropdown-menu {
            display: none;
            position: absolute;
            top: 50px;
            right: 0;
            background: var(--bg-color);
            border-radius: 12px;
            box-shadow: 0 8px 24px rgba(0, 0, 0, 0.15);
            z-index: 1000;
            flex-direction: column;
            gap: 0.5rem;
            padding: 0.75rem;
            opacity: 0;
            transform: translateY(-10px);
            transition: opacity 0.2s ease, transform 0.2s ease;
overflow: hidden; /* Add this line to prevent content overflow */
        }
        

        .dropdown-menu.show {
            display: flex;
            opacity: 1;
            transform: translateY(0);
        }

        .dropdown-menu .icon-button {
            width: 100%;
            border-radius: 8px;
            justify-content: flex-start;
            padding: 0.75rem 1rem;
            background: transparent;
            color: var(--text-color);
            font-size: 0.95rem;
            transition: all 0.2s ease;
            display: flex;
            align-items: center;
            gap: 0.75rem;
        white-space: nowrap; /* Prevent text from wrapping */
            overflow: hidden;      /* Hide any overflowing text */
            text-overflow: ellipsis; /* Add ellipsis (...) for truncated text */
        }

        .dropdown-menu .icon-button:hover {
            background: rgba(0, 0, 0, 0.05);
        }

        .dropdown-menu .icon-button:active {
            background: rgba(0, 0, 0, 0.1);
        }

        /* Dark Mode Styles for Dropdown */
        body.dark-mode .dropdown-menu {
            background: var(--bg-color);
            box-shadow: 0 8px 24px rgba(255, 255, 255, 0.1);
        }

        body.dark-mode .dropdown-menu .icon-button {
            color: var(--text-color);
        }

        body.dark-mode .dropdown-menu .icon-button:hover {
            background: rgba(255, 255, 255, 0.05);
        }

        body.dark-mode .dropdown-menu .icon-button:active {
            background: rgba(255, 255, 255, 0.1);
        }
<button id="calendar-button" class="icon-button">📅</button>

<!-- Add this right before the closing </body> tag -->
<div id="calendar-modal" class="calendar-modal">
    <div class="calendar-content">
        <div class="calendar-header">
            <button id="prev-month" class="calendar-nav-button">&lt;</button>
            <h2 id="current-month-year"></h2>
            <button id="next-month" class="calendar-nav-button">&gt;</button>
        </div>
        <div class="calendar-grid">
            <div class="calendar-weekdays">
                <div>Sun</div>
                <div>Mon</div>
                <div>Tue</div>
                <div>Wed</div>
                <div>Thu</div>
                <div>Fri</div>
                <div>Sat</div>
            </div>
            <div class="calendar-days" id="calendar-days"></div>
        </div>
    </div>
</div>

<!-- Add this CSS to the style section -->
<style>
    /* Calendar Styles */
    .calendar-modal {
        display: none;
        position: fixed;
        top: 50%;
        left: 50%;
        transform: translate(-50%, -50%);
        background: var(--bg-color);
        border-radius: 16px;
        padding: 1.5rem;
        box-shadow: 0 8px 32px rgba(0, 0, 0, 0.2);
        z-index: 1000;
        width: 350px;
        backdrop-filter: blur(10px);
    }

    .calendar-modal.show {
        display: block;
    }

    .calendar-header {
        display: flex;
        justify-content: space-between;
        align-items: center;
        margin-bottom: 1rem;
    }

    .calendar-nav-button {
        background: none;
        border: none;
        color: var(--text-color);
        font-size: 1.2rem;
        cursor: pointer;
        padding: 0.5rem;
        border-radius: 8px;
        transition: background 0.2s ease;
    }

    .calendar-nav-button:hover {
        background: rgba(0, 0, 0, 0.1);
    }

    .calendar-grid {
        display: grid;
        grid-template-columns: repeat(7, 1fr);
        gap: 4px;
    }

    .calendar-weekdays {
        display: contents;
        font-weight: 600;
        color: var(--text-color);
        text-align: center;
        margin-bottom: 0.5rem;
    }

    .calendar-weekdays div {
        padding: 0.5rem;
        font-size: 0.9rem;
    }

    .calendar-days {
        display: grid;
        grid-template-columns: repeat(7, 1fr);
        gap: 4px;
    }

    .calendar-day {
        padding: 0.8rem;
        text-align: center;
        border-radius: 8px;
        cursor: pointer;
        transition: all 0.2s ease;
        background: rgba(0, 0, 0, 0.05);
        color: var(--text-color);
    }

    .calendar-day:hover {
        background: var(--primary-color);
        color: white;
    }

    .calendar-day.empty {
        background: transparent;
        cursor: default;
    }

    .calendar-day.today {
        background: var(--success-color);
        color: white;
        font-weight: bold;
    }

    body.dark-mode .calendar-day {
        background: rgba(255, 255, 255, 0.1);
    <style>
        /* Previous CSS remains the same */

        .note-button {
            padding: 0.5rem;
            border: none;
            border-radius: 50%;
            cursor: pointer;
            transition: all 0.2s ease;
            width: 32px;
            height: 32px;
            display: flex;
            align-items: center;
            justify-content: center;
        }

        .edit-button {
            background-color: var(--secondary-color);
            color: white;
        }

        .delete-button {
            background-color: var(--danger-color);
            color: white;
        }

        /* Add hover effects */
        .edit-button:hover {
            background-color: #7c79d6;
        }

        .delete-button:hover {
            background-color: #ff4757;
        }
/* Add this at the end of your CSS */
body.dark-mode .calendar-day {
    background: rgba(255, 255, 255, 0.1);
}
    </style>
</head>
<body>
<img id="background-image" class="background-media" alt="Background Image">
   <video id="background-video" class="background-media" autoplay muted loop>
    <source src="default-video.mp4" type="video/mp4">
    Your browser does not support the video tag.
</video>

    <div id="container">
        <section id="search-tile">
            <div id="search-container">
                <input type="text" id="google-search-bar" placeholder="Search Google...">
            </div>
        </section>

        <section id="notes-tile">
            <div id="header">
                <h1 id="title"><span>To-Dos</span> </h1>
                <div class="controls-container">
                    <button id="add-button">📝 Add</button>
                    <div class="menu-container">
                        <button id="menu-button" class="menu-button">☰</button>
                        <div id="dropdown-menu" class="dropdown-menu">
                            <label class="icon-button">
           <input type="file" id="video-upload" accept="video/*,image/*" hidden>
                                🎥 Background Media
                            </label>
                            <button id="dark-mode-toggle" class="icon-button">🌙 Dark Mode</button>
                            <button id="clear-storage" class="icon-button">🧹 Clear Storage</button>
                        </div>
                    </div>
                </div>
            </div>
            <div id="notes-list"></div>
        </section>
    </div>

<script> 
      
    const notesList = document.getElementById('notes-list');
    const addButton = document.getElementById('add-button');
    const darkModeToggle = document.getElementById('dark-mode-toggle');
    const videoUpload = document.getElementById('video-upload');
    const backgroundVideo = document.getElementById('background-video');
    const googleSearchBar = document.getElementById('google-search-bar');

     // Add event listener for '/' key press
    document.addEventListener('keydown', (event) => {
        if (event.key === '/') {
            googleSearchBar.focus(); // Focus on the search bar
            event.preventDefault(); // Prevent the '/' character from being entered
        }
    });
document.addEventListener('keydown', (e) => {
    if ((e.ctrlKey || e.metaKey) && e.key.toLowerCase() === 'z') {
        // Ctrl+Z or Cmd+Z pressed
        undoLastDelete();
    }
});
let undoStack = []; // Use a stack to store deleted notes and their data

    // Google Search Functionality (modified)
    googleSearchBar.addEventListener('keydown', (event) => {
        if (event.key === 'Enter') {
            const query = googleSearchBar.value.trim();
            if (query) {
                window.location.href = `https://www.google.com/search?q=${encodeURIComponent(query)}`;
                googleSearchBar.blur(); // Optionally remove focus after search
            } else {
                alert("Please enter a search term!");
            }
        }
        //If any key is pressed in search box other than enter then remove the focus from search box
        else{
            googleSearchBar.focus();
        }
    });

    // 1. CREATE NOTE ELEMENT FUNCTION (Place at the top of your script)
    function createNoteElement(noteText, isCompleted = false, isImportant = false) {
        const noteDiv = document.createElement('div');
        noteDiv.classList.add('note');
        if (isImportant) {  // Add important class here if needed
            noteDiv.classList.add('important');
        }
         // Complete checkbox
        const completeCheckbox = document.createElement('input');
        completeCheckbox.type = 'checkbox';
        completeCheckbox.classList.add('complete-checkbox');
        completeCheckbox.checked = isCompleted;
        completeCheckbox.addEventListener('change', () => {
            noteDiv.classList.toggle('completed', completeCheckbox.checked);
            saveNotes();
        });

        const noteContent = document.createElement('div');
        noteContent.classList.add('note-content');
        noteContent.textContent = noteText;
        noteDiv.appendChild(completeCheckbox);
        noteDiv.appendChild(noteContent);

        const noteActions = document.createElement('div'); // Create a container for actions
        noteActions.classList.add('note-actions');
        noteDiv.appendChild(noteActions); // Append to the note

        const deleteButton = document.createElement('button');
        deleteButton.classList.add('delete-button');
        deleteButton.innerHTML = '&#128465;'; // Dustbin icon
        noteDiv.appendChild(deleteButton);

deleteButton.addEventListener('click', () => {
    const noteData = { // Store the note's data, not just the element
        text: noteDiv.querySelector('.note-content').textContent,
        completed: noteDiv.classList.contains('completed'),
        important: noteDiv.classList.contains('important')
    };
    undoStack.push(noteData); // Add data to the undo stack
    noteDiv.remove(); // Remove the note from the DOM
    saveNotes();
});

document.addEventListener('keydown', (e) => {
    if ((e.ctrlKey || e.metaKey) && e.key.toLowerCase() === 'z') {
        undoLastDelete();
    }
});

function undoLastDelete() {
    if (undoStack.length > 0) {
        const noteData = undoStack.pop(); // Get the last deleted note data
        const noteElement = createNoteElement(noteData.text, noteData.completed, noteData.important); // Recreate the note element
        notesList.appendChild(noteElement); // Add the recreated note to the list
        saveNotes();
    }
}

 // *** PLACE THE STAR BUTTON AND DRAG-AND-DROP CODE HERE ***
    const starButton = document.createElement('button');
    starButton.classList.add('star-button');
    starButton.textContent = '☆'; // Or use an icon (e.g., '★')
    if (isImportant) {
        starButton.classList.add('active');
        noteDiv.classList.add('important');
    }

    starButton.addEventListener('click', () => {
        starButton.classList.toggle('active');
        noteDiv.classList.toggle('important');
        saveNotes();
    });

    noteActions.appendChild(starButton); // Add the star button to note actions


// DRAG-AND-DROP FUNCTIONALITY (STABLE VERSION)
let isDragging = false;
let startY;
let draggedNote;
let placeholder;
let initialIndex;

noteDiv.addEventListener('mousedown', (e) => {
    if (e.button !== 0) return; // Only left mouse button
    if (e.target.closest('input')) return; // Ignore if editing
    if (e.target.closest('.star-button')) return; // Check if target is star button
    if (e.target.closest('.delete-button')) return; // Check if target is delete button
    
    isDragging = true;
    draggedNote = noteDiv;
    initialIndex = Array.from(notesList.children).indexOf(noteDiv);

    const rect = noteDiv.getBoundingClientRect();
    startY = e.clientY - rect.top;

    // Create placeholder
    placeholder = document.createElement('div');
    placeholder.style.height = `${rect.height}px`;
    placeholder.style.margin = '1rem 0';
    placeholder.style.pointerEvents = 'none'; // Prevent placeholder from interfering
    notesList.insertBefore(placeholder, noteDiv.nextSibling);

    // Style dragged note
    draggedNote.style.position = 'fixed'; // Use fixed positioning for stability
    draggedNote.style.width = `${rect.width}px`; // Lock width to prevent resizing
    draggedNote.style.zIndex = 1000;
    draggedNote.style.top = `${rect.top}px`;
    draggedNote.style.left = `${rect.left}px`;
    draggedNote.style.transition = 'none'; // Disable transitions during drag
    draggedNote.classList.add('dragging');
});

document.addEventListener('mousemove', (e) => {
    if (!isDragging) return;

    const notes = Array.from(notesList.children).filter(n => n !== placeholder);
    const cursorY = e.clientY;

    // Calculate new position
    let newIndex = notes.findIndex(note => {
        const rect = note.getBoundingClientRect();
        return cursorY < rect.top + rect.height / 2;
    });

    if (newIndex === -1) newIndex = notes.length;

    // Update placeholder position
    if (newIndex < initialIndex) {
        notesList.insertBefore(placeholder, notes[newIndex]);
    } else {
        notesList.insertBefore(placeholder, notes[newIndex] || null);
    }

    // Smoothly move the dragged note
    draggedNote.style.top = `${e.clientY - startY}px`;
});

document.addEventListener('mouseup', () => {
    if (!isDragging) return;

    // Cleanup
    isDragging = false;
    notesList.replaceChild(draggedNote, placeholder);
    placeholder.remove();

    draggedNote.style.removeProperty('position');
    draggedNote.style.removeProperty('z-index');
    draggedNote.style.removeProperty('top');
    draggedNote.style.removeProperty('left');
    draggedNote.style.removeProperty('width');
    draggedNote.style.removeProperty('transition');
    draggedNote.classList.remove('dragging');

    saveNotes();
});
        
// Event Delegation for Note Actions (Improved for right-click edit)
notesList.addEventListener('contextmenu', (event) => {  // Use contextmenu event
    const target = event.target;
    const noteDiv = target.closest('.note');

    if (noteDiv && target.classList.contains('note-content')) { // Only edit on right-click of note content
        event.preventDefault(); // Prevent default context menu
        const inputField = document.createElement('input');
        inputField.classList.add('edit-input');
        inputField.value = noteDiv.querySelector('.note-content').textContent;
        noteDiv.replaceChild(inputField, noteDiv.querySelector('.note-content'));
        inputField.focus();

        inputField.addEventListener('blur', () => saveEdit(noteDiv, inputField));
        inputField.addEventListener('keydown', (event) => {
            if (event.key === 'Enter') {
                saveEdit(noteDiv, inputField);
            }
        });
    }
});

        if (isCompleted) {
            noteDiv.classList.add('completed');
        }

        return noteDiv;
    }

    // Function to save edited note
    function saveEdit(noteDiv, inputField) {
        const newText = inputField.value;
        const noteContent = document.createElement('div');
        noteContent.classList.add('note-content');
        noteContent.textContent = newText;
        noteDiv.replaceChild(noteContent, inputField);
        saveNotes();
    }

    // Add note button event listener
    addButton.addEventListener('click', () => {
        const noteText = prompt("Enter your note:");
        if (noteText && noteText.trim()) {
            const noteElement = createNoteElement(noteText.trim());
            notesList.appendChild(noteElement);
            saveNotes();
        } else {
            alert("Note cannot be empty!");
        }
    });

    // Dark mode toggle event listener
    darkModeToggle.addEventListener('click', () => {
        document.body.classList.toggle('dark-mode');
        document.getElementById('container').classList.toggle('dark-mode');
        const notes = document.querySelectorAll('.note');
        notes.forEach(note => {
            note.classList.toggle('dark-mode');
        });

        // Save dark mode state to localStorage
        const isDarkMode = document.body.classList.contains('dark-mode');
        localStorage.setItem('darkMode', isDarkMode);
    });

    // Load dark mode state from localStorage
    const savedDarkMode = localStorage.getItem('darkMode');
    if (savedDarkMode === 'true') {
        document.body.classList.add('dark-mode');
        document.getElementById('container').classList.add('dark-mode');
        const notes = document.querySelectorAll('.note');
        notes.forEach(note => {
            note.classList.add('dark-mode');
        });
    }

    // Function to save notes to localStorage
function saveNotes() {
    const notes = [];
    const noteElements = notesList.children; // Get the children of notesList
    for (let i = 0; i < noteElements.length; i++) { // Iterate through them
        const noteElement = noteElements[i];
        const noteContent = noteElement.querySelector('.note-content').textContent;
        const isCompleted = noteElement.querySelector('.complete-checkbox').checked;
        const isImportant = noteElement.classList.contains('important'); // Get importance
        notes.push({ text: noteContent, completed: isCompleted, important: isImportant});
    }
    localStorage.setItem('notes', JSON.stringify(notes));
}

    // Function to load notes from localStorage
   function loadNotes() {
    const savedNotes = localStorage.getItem('notes');
    if (savedNotes) {
        const notes = JSON.parse(savedNotes);
        notes.forEach(note => {
            const noteElement = createNoteElement(note.text, note.completed, note.important);
            notesList.appendChild(noteElement); // Append in correct order
        });
    }
}

    // Load notes when the page loads
    loadNotes();

    // Video upload event listener
videoUpload.addEventListener('change', (event) => {
    const file = event.target.files[0];
    if (file) {
        const fileType = file.type;
        const isValidType = fileType.startsWith('video') || fileType.startsWith('image');
        
        if (!isValidType) {
            alert('Please select a valid video or image file');
            return;
        }

        saveMediaToIndexedDB(file, fileType);
        const mediaURL = URL.createObjectURL(file);
        
        if (fileType.startsWith('image')) {
            document.getElementById('background-image').src = mediaURL;
            document.getElementById('background-image').classList.add('active');
            document.getElementById('background-video').classList.remove('active');
        } else {
            document.getElementById('background-video').src = mediaURL;
            document.getElementById('background-video').classList.add('active');
            document.getElementById('background-image').classList.remove('active');
        }
    }
});

    // IndexedDB setup
    const dbName = "VideoOrganizerDB";
    const storeName = "backgroundMedia";
    let db;

    // Open or create the IndexedDB database
    const request = indexedDB.open(dbName, 2);

    request.onupgradeneeded = (event) => {
        db = event.target.result;
        if (!db.objectStoreNames.contains(storeName)) {
            db.createObjectStore(storeName);
        }
    };

request.onsuccess = (event) => {
    db = event.target.result;
    loadMediaFromIndexedDB(); // Correct function name
};

    request.onerror = (event) => {
        console.error("Error opening IndexedDB:", event.target.error);
    };

    // Function to save video to IndexedDB
    function saveMediaToIndexedDB(file, type) {
        const transaction = db.transaction(storeName, "readwrite");
    const store = transaction.objectStore(storeName);
    const mediaData = { file, type };
    const request = store.put(mediaData, "backgroundMedia");

        request.onsuccess = () => {
            console.log("Media saved to IndexedDB");
        if (type.startsWith('image')) {
            document.getElementById('background-image').classList.add('active');
            document.getElementById('background-video').classList.remove('active');
        } else {
            document.getElementById('background-video').classList.add('active');
            document.getElementById('background-image').classList.remove('active');
        }
    };
}


    // Function to load media from IndexedDB
function loadMediaFromIndexedDB() {
    const transaction = db.transaction(storeName, "readonly");
    const store = transaction.objectStore(storeName);
    const request = store.get("backgroundMedia");

    request.onsuccess = (event) => {
        const mediaData = event.target.result;
        if (mediaData) {
            const url = URL.createObjectURL(mediaData.file);
            if (mediaData.type.startsWith('image')) {
                document.getElementById('background-image').src = url;
                document.getElementById('background-image').classList.add('active');
            } else {
                document.getElementById('background-video').src = url;
                document.getElementById('background-video').classList.add('active');
            }
        }
    };
}

videoUpload.addEventListener('change', (event) => {
    const file = event.target.files[0];
    if (file) {
        const fileType = file.type;
        const isValidType = fileType.startsWith('video') || fileType.startsWith('image');
        
        if (!isValidType) {
            alert('Please select a valid video or image file');
            return;
        }

        saveMediaToIndexedDB(file, fileType);
        const mediaURL = URL.createObjectURL(file);
        
        if (fileType.startsWith('image')) {
            document.getElementById('background-image').src = mediaURL;
            document.getElementById('background-image').classList.add('active');
            document.getElementById('background-video').classList.remove('active');
        } else {
            document.getElementById('background-video').src = mediaURL;
            document.getElementById('background-video').classList.add('active');
            document.getElementById('background-image').classList.remove('active');
        }
    }
});

   // Clear storage event listener
document.getElementById('clear-storage').addEventListener('click', () => {
    const transaction = db.transaction(storeName, "readwrite");
    const store = transaction.objectStore(storeName);
    const request = store.delete("backgroundMedia");

    request.onsuccess = () => {
        console.log("Media cleared from IndexedDB");
        document.getElementById('background-image').classList.remove('active');
        document.getElementById('background-video').classList.remove('active');
        document.getElementById('background-video').src = '';
        document.getElementById('background-image').src = '';
        // Clear current file from input
        videoUpload.value = '';
        location.reload();
    };

    request.onerror = (event) => {
        console.error("Error clearing media:", event.target.error);
    };
});
    // Dropdown menu functionality
    const menuButton = document.getElementById('menu-button');
    const dropdownMenu = document.getElementById('dropdown-menu');

    menuButton.addEventListener('click', () => {
        dropdownMenu.classList.toggle('show');
    });

    // Close the dropdown menu if clicked outside
    window.addEventListener('click', (event) => {
        if (!event.target.matches('.menu-button') && !event.target.matches('.dropdown-menu *')) {
            dropdownMenu.classList.remove('show');
        }
    });//developer far lion☺️👍
</script>

</body>
</html>
