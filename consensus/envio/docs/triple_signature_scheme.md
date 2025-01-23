## Handling Unauthorized Signatures

### Verification of Signatures

Each block in the blockchain includes metadata specifying the validators selected for signing that block. This metadata contains the public keys of the three chosen validators. Here's how the process works:

1. **Block Creation and Signing:**
   - When a new block is created, it includes:
     - Block header.
     - Transaction data.
     - Metadata specifying the selected validators (public keys).
     - Space for three signatures.
   - The chosen validators sign the block with their private keys.

2. **Broadcasting the Block:**
   - Once the block is signed by the three chosen validators, it is broadcasted to the network.

3. **Block Reception and Verification:**
   - When a node receives a block, it performs the following checks:
     1. **Signature Validation:** The node verifies that the signatures match the public keys of the selected validators specified in the block metadata.
        - This involves using cryptographic algorithms to check the signatures. For example, if ECDSA (Elliptic Curve Digital Signature Algorithm) is used, the node would verify that the signatures are valid for the given public keys.
     2. **Validator Check:** The node ensures that the validators who signed the block are indeed the ones chosen for that block. If any signature does not match the selected validators, the block is rejected.

### Penalizing Unauthorized Actions

If an unauthorized validator attempts to sign and broadcast a block, the following steps are taken:

1. **Detection:**
   - The network nodes detect the unauthorized signature during the verification process. Since the block metadata clearly defines the selected validators, any deviation is easily spotted.

2. **Rejection:**
   - The block containing an unauthorized signature is immediately rejected by the nodes. It will not be added to the blockchain.

3. **Penalties:**
   - Validators who sign blocks without authorization face penalties:
     - **Slashing:** A portion of the unauthorized validator’s stake is forfeited.
     - **Temporary or Permanent Ban:** The validator may be temporarily or permanently banned from participating in future validation processes.

### Consensus Rules

The consensus mechanism strictly enforces that only the selected validators can sign a block. If a validator deviates from this protocol, the consensus rules dictate penalties, which might include slashing and banning as mentioned earlier.

By implementing these technical measures, the integrity of the triple-signature scheme is maintained, ensuring that only the designated validators contribute to block confirmation and preventing unauthorized signatures from disrupting the network.
