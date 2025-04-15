<!-- hide -->
# Build a Memory Game with React: Find the Pairs!
<!-- endhide -->

<how-to-start>
  
## 🌱 How to start this project?

Do not clone this repository because we will use a different template.

We recommend opening the `React template` using a provisioning tool like [Codespaces](https://4geeks.com/lesson/what-is-github-codespaces) (recommended) or [Gitpod](https://4geeks.com/lesson/how-to-use-gitpod). Alternatively, you can [clone the GitHub repository](https://4geeks.com/how-to/github-clone-repository) on your local computer using the `git clone` command.

This is the repository you need to open or clone:

```
https://github.com/4GeeksAcademy/react-hello
```

> ⚠ You will need to have Node.js installed if you do it locally, but all of that is already installed on Codespaces or Gitpod!

</how-to-start>

## 📝 Instructions

### Step 1: Set Up the Project

- [ ] Set up the boilerplate project from the provided React template.
  
- [ ] Follow the instructions in the README of the repository to set up your development environment.

### Step 2: Plan the Game Structure

- [ ] Create a sketch or diagram of how your memory game will be structured.
  - How many cards will there be?
  - How will you represent the cards in the state?
  - What properties will you need for each card (e.g., id, image, flipped state)?

### Step 3: Implement the Game Board

- [ ] Create a `Board` component that will contain the cards.

- [ ] Create a `Card` component that will represent each individual card.

- [ ] Generate a set of cards with matching pairs and shuffle them randomly.

```jsx
// Example of card generation
const cards = [
  { id: 1, image: 'url1', matched: false },
  { id: 1, image: 'url1', matched: false },
  // ... more cards
];
```

### Step 4: Manage Card State with useState

- [ ] Use the `useState` hook to manage the state of the cards in the `Board` component.

- [ ] Create states for:
  - The currently flipped cards.
  - The cards that have been matched (correct pairs).
  - The number of attempts or moves made (optional).

```jsx
const [cards, setCards] = useState([]);
const [flippedCards, setFlippedCards] = useState([]);
const [matchedCards, setMatchedCards] = useState([]);
```

### Step 5: Implement Game Logic with useEffect

- [ ] Use the `useEffect` hook to check if the two flipped cards are a pair.

- [ ] If the cards match, update the state to reflect that they have been found.

- [ ] If they don't match, flip the cards back over after a brief delay.

```jsx
useEffect(() => {
  if (flippedCards.length === 2) {
    const [firstCard, secondCard] = flippedCards;
    if (firstCard.id === secondCard.id) {
      setMatchedCards([...matchedCards, firstCard.id]);
    }
    setTimeout(() => setFlippedCards([]), 1000);
  }
}, [flippedCards]);
```

### Step 6: Add Click Event Handling

- [ ] In the `Card` component, add an `onClick` event that handles when a card is selected.

- [ ] Make sure you cannot flip more than two cards at a time and that you cannot select the same card twice!

```jsx
const handleCardClick = (card) => {
  if (flippedCards.length < 2 && !flippedCards.includes(card)) {
    setFlippedCards([...flippedCards, card]);
  }
};
```

### Step 7: Add Simple Animations

- [ ] Use CSS to add transitions or animations when the cards are flipped.

- [ ] You can change the CSS class of the card based on its state (flipped or not) and apply styles accordingly.

```css
.card {
  transition: transform 0.6s;
  transform-style: preserve-3d;
}

.card.flipped {
  transform: rotateY(180deg);
}
```

### Step 8: Improve the User Interface

- [ ] Add visual elements like a move counter or a timer!

- [ ] Ensure the game is responsive and looks good on different screen sizes.

## Bonus Section

### Additional Features to Practice and Improve the Project:

1. **Score Counter:** Implement a scoring system based on the number of moves or the time it takes the player to complete the game!

2. **Difficulty Levels:** Add different difficulty levels with more or fewer cards.

3. **Sounds and Effects:** Add sound effects when flipping cards or finding a pair!

4. **Save Progress:** Allow the player to pause and continue the game by saving the state in local storage.

5. **Customizable Theme:** Let the player choose between different themes or sets of images for the cards!

6. **Multiplayer Game:** Implement a mode where two players compete in turns and record who finds more pairs.

Explore different enhancements to make your memory game more interactive and entertaining!
