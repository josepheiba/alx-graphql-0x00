# Character Queries

This directory contains GraphQL queries to retrieve character information from the Rick and Morty API.

## Files:

### Individual Character Queries:
- `character-id-1.graphql` - Query for character with ID 1
- `character-id-1-output.json` - Expected output for character ID 1
- `character-id-2.graphql` - Query for character with ID 2
- `character-id-2-output.json` - Expected output for character ID 2
- `character-id-3.graphql` - Query for character with ID 3
- `character-id-3-output.json` - Expected output for character ID 3
- `character-id-4.graphql` - Query for character with ID 4
- `character-id-4-output.json` - Expected output for character ID 4

### Character List Queries (Paginated):
- `characters-page-1.graphql` - Query for characters page 1
- `characters-page-1-output.json` - Expected output for characters page 1
- `characters-page-2.graphql` - Query for characters page 2
- `characters-page-2-output.json` - Expected output for characters page 2
- `characters-page-3.graphql` - Query for characters page 3
- `characters-page-3-output.json` - Expected output for characters page 3
- `characters-page-4.graphql` - Query for characters page 4
- `characters-page-4-output.json` - Expected output for characters page 4

## Usage:

### Individual Character Queries
These queries fetch specific character details using their ID, including:
- id
- name
- status
- species
- type
- gender

### Character List Queries
These queries fetch paginated lists of characters, including:
- id
- name
- status
- image
