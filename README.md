# RIP-7560 Landing Page

A static HTML landing page for RIP-7560 - Native Account Abstraction.

## About

RIP-7560 is an account abstraction proposal based on ERC-4337 that introduces consensus-layer protocol changes, instead of relying on higher-layer infrastructure.

## Features

- ✅ **Static HTML** - No build process required
- ✅ **Responsive Design** - Works on all devices
- ✅ **Dark Mode Support** - Automatically adapts to system preference
- ✅ **GitHub Pages Ready** - Deploy directly to GitHub Pages
- ✅ **Free Hosting** - No server costs

## Quick Start

### Local Development

1. Clone the repository
2. Open `index.html` in your browser, or run:
   ```bash
   python3 -m http.server 3000
   ```
3. Visit `http://localhost:3000`

### Deployment

This site is designed to be deployed to GitHub Pages. See `MIGRATION_GUIDE.md` for detailed deployment instructions.

## Project Structure

```
7560-landing-page/
├── index.html              # Main landing page
├── assets/                 # Static assets
│   ├── ERC-4337-team-logo-color.svg
│   └── ERC-4337-team-logo-color-light.svg
├── .github/workflows/      # GitHub Actions deployment
│   └── deploy.yml
└── README.md              # This file
```

## Links

- **Read**: [Official RIP on GitHub](https://github.com/ethereum/RIPs/blob/master/RIPS/rip-7560.md)
- **Discuss**: [Fellowship of Ethereum Magicians](https://ethereum-magicians.org/t/rip-7560-native-account-abstraction/16664)
- **Follow**: [@rip7560 on X](https://x.com/rip7560)
- **Discover**: [ERC-4337](https://erc4337.io)

## License

This project is open source and available under the [MIT License](LICENSE).
