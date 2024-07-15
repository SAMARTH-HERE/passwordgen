
# Password Generator

A simple password generator built with React. This project allows users to generate a random password with customizable options for including numbers and special characters.

## Features

- Generate passwords with a customizable length
- Option to include numbers
- Option to include special characters
- Copy generated password to clipboard

## Getting Started

### Prerequisites

- Node.js and npm installed on your machine

### Installation

1. Clone the repository:

   ```bash
   git clone https://github.com/your-username/password-generator.git
   ```

2. Navigate to the project directory:

   ```bash
   cd password-generator
   ```

3. Install the dependencies:

   ```bash
   npm install
   ```

### Running the App

To start the development server, run:

```bash
npm run dev
```

Open your browser and go to `http://localhost:3000` to see the app in action.

### Usage

1. Adjust the password length using the range slider.
2. Check the boxes to include numbers and/or special characters in the generated password.
3. Click the "Generate" button to create a new password.
4. Click the "COPY" button to copy the generated password to your clipboard.

## Code Overview

### `App.js`

This is the main component of the app. It includes state management and the password generation logic.

```javascript
import { useState, useCallback } from 'react';
import './App.css';

function App() {
  const [size, setSize] = useState(8);
  const [number, setNumber] = useState(false);
  const [characters, setCharacters] = useState(false);
  const [password, setPassword] = useState('');

  const passwordGenerator = useCallback(() => {
    let pass = '';
    let str = 'ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz';

    if (number) {
      str += '1234567890';
    }

    if (characters) {
      str += '~!@#$%^&*()-_=+[{]}\\|';
    }

    for (let i = 0; i < size; i++) {
      let char = Math.floor(Math.random() * str.length);
      pass += str.charAt(char);
    }

    setPassword(pass);
  }, [number, characters, size]);

  return (
    <div className="">
      <div className="h-40 w-3/6 bg-yellow-600 rounded-lg">
        <br />
        <br />
        <div className="flex gap-5 mx-10">
          <input className="" type="text" value={password} readOnly />
          <button type="button" className="bg-red-500 h-10 w-20" onClick={() => navigator.clipboard.writeText(password)}>COPY</button>
        </div>
        <br />
        <div className="flex flex-row gap-5 mx-10">
          <input type="range" min={0} max={100} value={size} onChange={(e) => setSize(Number(e.target.value))} />
          <h4>Length ({size})</h4>
          <input type="checkbox" checked={number} onChange={(e) => setNumber(e.target.checked)} />
          <h4>Numbers</h4>
          <input type="checkbox" checked={characters} onChange={(e) => setCharacters(e.target.checked)} />
          <h4>Characters</h4>
        </div>
        <br />
        <button className="bg-blue-500 h-10 w-20 mx-10" onClick={passwordGenerator}>Generate</button>
      </div>
    </div>
  );
}

export default App;
```

### `App.css`

This file contains the styles for the app. Customize it to fit your design preferences.

```css
body {
  font-family: Arial, sans-serif;
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
  margin: 0;
}

h4 {
  margin: 0;
}

input[type="text"] {
  width: 60%;
  padding: 0.5rem;
  border: 2px solid black;
}

button {
  cursor: pointer;
}

.container {
  display: flex;
  flex-direction: column;
  align-items: center;
}
```

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

## Acknowledgments

- [React](https://reactjs.org/)
- [Vite](https://vitejs.dev/)
```

