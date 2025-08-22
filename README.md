# viem-dapp-starter

Features
🔗 Quai Network integration
🦊 Pelagus wallet connection
⚡ Vite + React + TypeScript
🎨 TailwindCSS styling
📦 Custom Quai transport for Viem
🔄 Network switching support
🛡️ Type-safe transaction handling
Prerequisites
Node.js (v16 or higher)
NPM or Yarn
Pelagus Wallet browser extension
Quick Start
Clone the repository:
git clone https://github.com/dominant-strategies/quai-viem-dapp-starter
cd quai-viem-dapp-starter
Install dependencies:
npm install
Start the development server:
npm run dev
Open your browser and navigate to http://localhost:5173
Project Structure
quai-viem-dapp-starter/
├── src/
│   ├── components/
│   │   └── PelagusWalletApp.tsx    # Main wallet component
│   ├── formatter.ts                 # Quai Network formatters
│   ├── quaiTransport.ts            # Custom Viem transport
│   ├── App.tsx                     # Root component
│   ├── main.tsx                    # Entry point
│   ├── index.css                   # Global styles
│   └── vite-env.d.ts              # Type declarations
├── index.html
├── package.json
├── tsconfig.json
├── vite.config.ts
├── tailwind.config.js
└── README.md
Key Components
Custom Quai Transport
The DApp includes a custom transport layer that maps Ethereum RPC methods to their Quai equivalents:

export function createQuaiTransport(provider: any) {
  return custom({
    async request({ method, params }: RpcRequest) {
      const mappedMethod = method === 'eth_chainId' ? 'quai_chainId' : method
      return provider.request({
        method: mappedMethod,
        params
      })
    }
  })
}
Wallet Integration
The template provides a complete wallet integration component with:

Wallet connection
Network switching
Transaction sending
Error handling
Event listeners for account and chain changes
Available Scripts
npm run dev - Start development server
npm run build - Build for production
npm run preview - Preview production build
npm run typecheck - Run TypeScript type checking
Configuration
Quai Network Settings
The default configuration connects to the Quai Network. You can modify the chain settings in formatter.ts:

export const quaiChain = {
  id: 9000,
  name: 'Quai Network',
  nativeCurrency: {
    decimals: 18,
    name: 'QUAI',
    symbol: 'QUAI',
  },
  rpcUrls: {
    default: {
      http: ['http://localhost:9200'],
    },
    public: {
      http: ['https://rpc.quai.network/cyprus1'],
    },
  },
  formatters,
} as const satisfies Chain
Environment Variables
Create a .env file in the root directory:

VITE_RPC_URL=https://rpc.quai.network/cyprus1
TypeScript Support
The template includes full TypeScript support with:

Custom type definitions for Pelagus wallet
Viem type extensions
Proper error handling types
Strict type checking
Contributing
Contributions are welcome! Please feel free to submit a Pull Request.

License
MIT License - see LICENSE file for details

Acknowledgments
Viem Documentation
Quai Network Documentation
Pelagus Wallet
Support
For support, please join the Quai Network Discord or open an issue in this repository.

Remember to update the package.json, clean up unused dependencies, and add proper error handling before deploying to production.
