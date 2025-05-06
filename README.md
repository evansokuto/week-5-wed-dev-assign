# week-5-wed-dev-assign

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1" />
    <title>Dynamic DOM Manipulation</title>
    <link rel="stylesheet" href="styles.css" />
</head>
<body>
    <header>
        <h1 id="main-title">Welcome to My Dynamic Page</h1>
    </header>

    <nav>
        <button id="change-text-btn">Change Header Text</button>
        <button id="toggle-box-btn">Add/Remove Box</button>
        <button id="change-style-btn">Change Box Style</button>
    </nav>

    <main>
        <section id="content-section">
            <p>This paragraph will be dynamically updated.</p>
        </section>
    </main>

    <footer>
        <small>&copy; 2025 My Dynamic Page</small>
    </footer>

    <script src="script.js"></script>
</body>
</html>



js script

// Select elements
const mainTitle = document.getElementById('main-title');
const changeTextBtn = document.getElementById('change-text-btn');
const toggleBoxBtn = document.getElementById('toggle-box-btn');
const changeStyleBtn = document.getElementById('change-style-btn');
const contentSection = document.getElementById('content-section');

let boxExists = false;
let boxElement = null;

// Change header text dynamically
changeTextBtn.addEventListener('click', () => {
    if (mainTitle.textContent === 'Welcome to My Dynamic Page') {
        mainTitle.textContent = 'You clicked the Change Text button!';
    } else {
        mainTitle.textContent = 'Welcome to My Dynamic Page';
    }
});

// Add or remove a box element dynamically
toggleBoxBtn.addEventListener('click', () => {
    if (!boxExists) {
        boxElement = document.createElement('div');
        boxElement.id = 'dynamic-box';
        boxElement.textContent = 'I am a dynamically added box!';
        boxElement.style.padding = '20px';
        boxElement.style.marginTop = '20px';
        boxElement.style.backgroundColor = '#f0f0f0';
        boxElement.style.border = '2px solid #333';
        contentSection.appendChild(boxElement);
        boxExists = true;
    } else {
        contentSection.removeChild(boxElement);
        boxElement = null;
        boxExists = false;
    }
});

// Change CSS styles of the box dynamically
changeStyleBtn.addEventListener('click', () => {
    if (boxExists && boxElement) {
        // Toggle between two styles
        if (boxElement.style.backgroundColor === 'lightblue') {
            boxElement.style.backgroundColor = '#f0f0f0';
            boxElement.style.color = '#000';
            boxElement.style.borderRadius = '0';
        } else {
            boxElement.style.backgroundColor = 'lightblue';
            boxElement.style.color = 'white';
            boxElement.style.borderRadius = '10px';
        }
    } else {
        alert('Please add the box first by clicking "Add/Remove Box" button.');
    }
});
