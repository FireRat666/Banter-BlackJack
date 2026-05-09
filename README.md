# Banter BlackJack!

A fully functional BlackJack game for Banter spaces.

## Features
- Support for 1-7 players.
- Persistent state management via BanterSpace.
- Configurable position, rotation, and instance names.
- Automatic hand management and turn handling.
- Double Down and Split options.
- Host migration and disconnect handling.

## How to add to your space

To add BlackJack to your Banter space, simply include the `blackjack.js` script in your HTML file. You can configure its placement and behavior using attributes on the `<script>` tag.

### Basic Implementation

```html
<script src="https://blackjack.firer.at/blackjack.js"
        position="0 0 0"
        rotation="0 0 0"
        instance="my-blackjack-game"></script>
```

### Script Parameters

| Parameter | Default | Description |
| :--- | :--- | :--- |
| `position` | `0 0 2` | The world position where the BlackJack table will be spawned (X Y Z). |
| `rotation` | `0 0 0` | The rotation of the BlackJack table (Euler angles: X Y Z). |
| `instance` | `blackjack_game` | A unique identifier for the game state. Use different instance IDs if you want multiple independent games in the same space. |
| `debug` | `false` | Enables debug logging in the console if set to `true`. |

## Example `index.html`

```html
<!DOCTYPE html>
<html>
  <head>
    <meta property="og:title" content="My Banter Space">
  </head>
  <body>
    <!-- Load BlackJack Game -->
    <script src="https://blackjack.firer.at/blackjack.js"
            position="0 0 2"
            rotation="0 180 0"
            instance="lobby-bj"></script>
  </body>
</html>
```

## Attribution

This BlackJack game is based on previous works:
*   **Original "Holograms Against Humanity" (AltspaceVR adaptation):** Derogatory, falkrons, schmidtec
*   **Ported to Banter:** Shane
*   **improved, Fixed and ported from A-Frame:** FireRat

The sound assets used in this project are derived from the original "Holograms Against Humanity" project.

## How it works

The game uses the Banter SDK to create game objects, UI elements, and manage network state.

1. **Initialization**: The script reads parameters from its own tag or URL search params.
2. **Environment**: It builds the BlackJack table and player areas.
3. **State**: Game state is synchronized across all players using `BS.BanterScene` state events.
4. **Gameplay**: Players join, place bets, and play their hands (Hit, Stand, Double Down, Split). The dealer then plays according to standard rules.
5. **Host Management**: The game automatically handles host migration if the current host leaves.
