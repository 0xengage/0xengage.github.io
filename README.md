Welcome to 0xEngage's documentation page.

### What is 0xEngage?
0xengage is a Solana protocol to allow dapps and wallets to communicate with each other.

### How does it work?
Protocol details are coming soon.

### Installation


```bash
npm install -g @0xengage/client
```

### Quickstart


```typescript

import { Mailbox } from '@0xengage/client';

..
..

// Initialize mailbox for `receiver` address
const mailbox = new Mailbox(conn, { receiver, payer, });

// Send messages
await mailbox.send("text0");
await mailbox.send("text1");

// Fetch messages
const messages = await mailbox.fetch();

// If `receiver` is a Keypair, can call pop to close
// message accounts and retrieve rent (goes to receiver)
await mailbox.pop();
await mailbox.pop();
```
