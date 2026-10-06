# Pong: Player vs Computer

A small, single-player Pong game built with HTML, CSS, vanilla JavaScript, and the HTML5 Canvas API. The complete game is in `index.html`; it has no dependencies, build step, or external assets.

## Run locally

1. Download or clone this repository.
2. Open `index.html` in a current desktop browser.

You can also serve the folder with any static web server and open its local URL. There is no installation step.

## Controls

- Move up: **W** or **↑**
- Move down: **S** or **↓**
- Pause or resume: **Space**
- Restart the match: **R**

The first side to reach seven points wins. To play again after a match, press **R**.

## Implementation notes

- The canvas uses a 900 × 560 logical playfield and scales responsively in the page. Muted pools of colored light and a few mirrored-tile glints give the dark background a restrained disco feel.
- The ball is drawn from Canvas primitives: a warm shaded surface, one curved seam, a small highlight, and a soft shadow. It is larger than a standard Pong ball for visibility. Rounded paddles use subdued contrasting colors.
- Player input is stored in a set of currently held keys and read every animation frame. This avoids depending on browser key-repeat events. Paddle positions are clamped to the playfield.
- The ball position advances using horizontal and vertical velocity (`dx`, `dy`). At the top and bottom edges, the vertical velocity reverses. A capped frame delta keeps movement stable if a browser frame is delayed.
- Paddle collision is checked manually as circle-to-axis-aligned-rectangle overlap. The ball is only reflected when moving toward the paddle, and is moved just outside the paddle after impact to prevent repeated collision on consecutive frames.
- The impact point on the paddle changes the bounce angle: hits near the center return flatter, while hits near either end send the ball at a steeper angle. Ball speed increases slightly after each paddle hit, up to a cap.
- The computer paddle follows the ball's vertical position with a speed limit and a small dead zone. Its finite movement speed gives the player a fair chance to aim shots away from it.
- When the ball crosses a goal line, the opposite side scores. After a short pause the ball returns to center and heads toward the side that just scored. The match ends at seven points.

## Repository contents

```text
index.html   Game markup, styling, rendering, input, and game logic
README.md    Setup, controls, and implementation notes
```

## Push to a public GitHub repository

Create an empty public repository on GitHub, then run these commands from this folder (replace the URL with your repository URL):

```bash
git init
git add index.html README.md
git commit -m "Build single-player Pong game"
git branch -M main
git remote add origin https://github.com/YOUR-USERNAME/YOUR-REPOSITORY.git
git push -u origin main
```

To publish the game as a website, enable GitHub Pages for the `main` branch and repository root in the repository's **Settings → Pages**.
