# Testing

This document outlines the testing strategy and execution commands for the Posh library.

## Testing Strategy

The Posh library utilizes the Amen testing framework to validate the integrity of its JavaScript exports and ensure the correct generation of CSS strings. 
The testing suite verifies that all exported properties map to the expected compiled stylesheet outputs.

## Running Tests

To run the automated tests, use the Genie task runner. 
The tests are executed in the Node environment.

```bash
npx genie test
```

If the Genie task is unavailable, you can fall back to the standard script:

```bash
npm run test
```
