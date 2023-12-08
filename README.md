# DynNFT BOT

This Python script is designed to interact with a blockchain, specifically for managing Dynamic Non-Fungible Tokens (NFTs) using smart contracts.
It includes various functionalities such as token burning, metadata creation, and image generation.
The script is intended to be run as a standalone Python program.
The script is heavily dependent on external services and the Ethereum blockchain.
Proper error handling and logging are implemented for robustness.
It's designed to work with a specific Ethereum smart contract,.
The script demonstrates advanced usage of Python for blockchain interactions and asynchronous programming.

## Here's an overview of the key components and functionalities:

### Import Libraries:
The script imports necessary libraries including json, os, asyncio, web3, dotenv, openai, requests, and datetime.
These libraries facilitate blockchain interaction, environment variable management, AI image generation, and basic file and time operations.

### Environment Setup:
It loads environment variables using dotenv, which includes configuration for blockchain interaction, OpenAI's API key, and other necessary parameters.

### Blockchain Setup:
Establishes a connection to the Ethereum blockchain using Web3.py and sets up the contract interaction using ABI and contract address fetched from environment variables.

### Function greet_time(value):
Based on the time of day, returns a corresponding IPFS hash.
This seems to be used for default image handling.

### Function burn_token(token_id): 
Implements a retry mechanism to burn (invalidate) a token on the blockchain.
It adjusts gas fees dynamically based on previous transaction costs to optimize for successful transactions.

### Function pinata_upload(filename): 
Uploads a file to Pinata, a service used for pinning files to IPFS (InterPlanetary File System), and returns the IPFS hash of the uploaded file.

### Function add_milliseconds_and_convert_to_unixtime(numbers):
It uses random numbers to generate additional time in milliseconds, converts this to a future datetime, and then to a Unix timestamp.
This is used to set expiration times for tokens.

### Function add_uris_to_token(token_id, uris, burnInSeconds): 
Updates a token with new URIs and a burn time in seconds on the blockchain.
It also includes retry logic with dynamic gas fee adjustments.

### Function generate_image_with_dalle(prompt):
Uses OpenAI's DALL-E to generate an image based on a prompt.

### Function save_image(image_url, filename):
Downloads an image from a URL and saves it locally.

### Function create_nft_metadata(...): 
Constructs and saves the metadata for an NFT, including details like token ID, image URL, and attributes derived from the blockchain event data.

### Event Handling (handle_event(event)): 
Listens to blockchain events related to NFT minting and randomness fulfillment, processes these events, and triggers corresponding actions (like image generation and metadata creation).

### Logging and Queue Processing: 
The script logs various events and processes a transaction queue, managing the order and execution of blockchain interactions.

### Asynchronous Main Function: 
Orchestrates the various components, setting up event filters and running the log loop, time logging, and transaction queue processing concurrently.

### Usage of Random Numbers (VRF):
The script uses random numbers for generating filenames and adding variability in token expiration times, enhancing the uniqueness and dynamic nature of each NFT.

### Security and Reliability: 
The script's design includes retry mechanisms with dynamic fee adjustments and error handling to ensure successful blockchain transactions,
important for maintaining the integrity and reliability of the NFT minting and management process.

Overall, this script represents a comprehensive solution for creating and managing Dynamic NFTs, utilizing AI for image generation and blockchain technology for secure and reliable token transactions.
