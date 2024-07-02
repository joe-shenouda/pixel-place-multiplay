# Pixel Place Multiplay

![Pixel Place Multiplay](https://i.postimg.cc/L4Tg8hWh/Schermafbeelding-2024-07-02-023245.png)

Pixel Place Multiplay is a multiplayer web application where users can collaborate to create pixel art. This project demonstrates real-time updates and collaboration using modern web technologies.

## Demo
Check out the live demo: [Pixel Place Multiplay](https://joe-shenouda.github.io/pixel-place-multiplay/)

## Table of Contents
- [Features](#features)
- [Technologies Used](#technologies-used)
- [Getting Started](#getting-started)
  - [Prerequisites](#prerequisites)
  - [Running Locally](#running-locally)
- [Usage](#usage)
- [Real-Time Data Synchronization](#real-time-data-synchronization)
- [Contributing](#contributing)
- [License](#license)
- [Acknowledgements](#acknowledgements)
- [Contact](#contact)

## Features
- Real-time pixel art collaboration
- Interactive grid for pixel art creation
- Responsive design for various devices
- User-friendly interface
- Multiple color options for drawing

## Technologies Used
- HTML5
- CSS3
- JavaScript (ES6+)
- WebSockets for real-time communication
- Node.js (for server)
- Express.js (for server framework)
- GUN for decentralized real-time database

## Getting Started

### Prerequisites
- Node.js (latest version recommended)
- npm (Node package manager)
- Web browser (latest version recommended)

### Running Locally
1. Clone the repository:
   ```bash
   git clone https://github.com/joe-shenouda/pixel-place-multiplay.git
   ```
2. Navigate to the project directory:
   ```bash
   cd pixel-place-multiplay
   ```
3. Install the dependencies:
   ```bash
   npm install
   ```
4. Start the server:
   ```bash
   npm start
   ```
5. Open `index.html` in your web browser.

## Usage
- Open the application in your web browser.
- Use the interactive grid to draw pixel art.
- Collaborate with other users in real-time.
- Choose different colors from the palette to create your artwork.

## Real-Time Data Synchronization
Pixel Place Multiplay uses [GUN](https://gun.eco/), a decentralized database, to enable real-time data synchronization. GUN allows data to be distributed across multiple nodes, creating a peer-to-peer network. In this project, we connect to a GUN relay server hosted at `https://gun-manhattan.herokuapp.com/gun`. This setup ensures that pixel updates are instantly synchronized across all connected users, providing a seamless collaborative experience. You can also set up and host your own GUN nodes if you prefer to manage your own data.

```javascript
const gun = Gun(['https://gun-manhattan.herokuapp.com/gun']);
const pixelsRef = gun.get('websim-rplace-pixels-5');
const tilesPlacedRef = gun.get('websim-rplace-tiles-placed');

pixelsRef.map().on(function(data, key) {
    if (data && !seenPixels.has(key)) {
        const [x, y] = key.split(',').map(Number);
        updatePixel(x, y, data.color);
        tilesPlaced++;
        document.getElementById('tiles-placed').textContent = tilesPlaced;
        seenPixels.add(key);
    }
});
```

## Contributing
Contributions are welcome! Follow these steps to contribute:
1. Fork the repository.
2. Create a new branch (`git checkout -b feature-branch`).
3. Make your changes.
4. Commit your changes (`git commit -m 'Add new feature'`).
5. Push to the branch (`git push origin feature-branch`).
6. Open a pull request.

## License
This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

## Acknowledgements
- Special thanks to all contributors and users for their support.
- Inspired by collaborative pixel art projects.

## Contact
For any inquiries, please contact Joe Shenouda via GitHub.

![GitHub Followers](https://img.shields.io/github/followers/joe-shenouda?style=social) ![GitHub Stars](https://img.shields.io/github/stars/joe-shenouda/pixel-place-multiplay?style=social)
