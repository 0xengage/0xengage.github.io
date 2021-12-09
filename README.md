Welcome to 0xEngage's documentation page.

### What is 0xEngage?
0xengage is a Solana protocol to allow dapps and wallets to communicate with each other.

### How does it work?
You can access 0xengage via `G3mefhJTnrSAtkrGFtztYeAo9nkM1kyNXkqaFkikfAmD` program on `devnet`.
More protocol details are coming soon.

### Installation


```bash
npm install @0xengage/client
```

### Quickstart


```typescript
import { Mailbox } from '@0xengage/client';

// Initialize mailbox for a receiver and start sending messages.
const mailbox = new Mailbox(conn, { receiverAddress, payer, });

// Send messages
await mailbox.send("text0");
await mailbox.send("text1");

// Fetch messages
// This returns:
// [
//  { sender: 'senders_public_key', data: 'text0' },
//  { sender: 'senders_public_key', data: 'text1' },
// ]
const messages = await mailbox.fetch();

// Receiver can close message accounts and retrieve rent.
const mailbox2 = new Mailbox(conn, { receiver, payer, });
await mailbox.pop();
await mailbox.pop();
```

### Transaction API


If you'd like to construct `Transaction` objects to interact with the 0xengage protocol,
but submit transactions to the network yourself, you can use the client as follows:


```typescript
import { Mailbox } from '@0xengage/client';

// Initialize mailbox for receiver
const mailbox = new Mailbox(conn, { receiverAddress, payerAddress, });

// Construct transactions to send messages. You may then submit
// `sendTx0` and `sendTx1` to the network. When submitting note
// that `payer` must sign the transaction.
const sendTx0 = await mailbox.makeSendTx("text0");
const sendTx1 = await mailbox.makeSendTx("text1");

// Fetch messages
// This returns:
// [
//  { sender: 'senders_public_key', data: 'text0' },
//  { sender: 'senders_public_key', data: 'text1' },
// ]
const messages = await mailbox.fetch();

// You can construct transactions to pop messages as follows. Note
// that receiver must sign the transaction in order for it to
// succeed.
const popTx0 = await mailbox.makePopTx();
const popTx1 = await mailbox.makePopTx();
```

### Contact
Join the community on the [0xEngage group](https://t.me/+tY-bKbPLixw1MmI5) on Telegram for questions or feedback.
