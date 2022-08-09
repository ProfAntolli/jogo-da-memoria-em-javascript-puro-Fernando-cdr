[![Open in Visual Studio Code](https://classroom.github.com/assets/open-in-vscode-c66648af7eb3fe8bc4f294546bfd86ef473780cde1dea487d3c4ff354943c9ae.svg)](https://classroom.github.com/online_ide?assignment_repo_id=8202027&assignment_repo_type=AssignmentRepo)
// scritps.js

const cards = document.querySelectorAll('.memory-card');

let hasFlippedCard = false; let lockBoard = false; let [firstCard, ], secondCard;

function flipCard() { if (lockBoard) return; if (this === firstCard) return;

this.classList.add('flip');

if (!hasFlippedCard) { hasFlippedCard = true; firstCard = this; return; }

secondCard = this; lockBoard = true;

checkForMatch(); }

function checkForMatch() { let isMatch = firstCard.dataset.framework === secondCard.dataset.framework; isMatch ? disableCards() : unflipCards(); }

function disableCards() { firstCard.removeEventListener('click', flipCard); secondCard.removeEventListener('click', flipCard);

resetBoard(); }

function unflipCards() { setTimeout(() => { firstCard.classList.remove('flip'); secondCard.classList.remove('flip');

resetBoard(); }, 1500); }

function resetBoard() { [hasFlippedCard, lockBoard] = [false, false]; [firstCard, secondCard] = [null, null]; }

+ (function shuffle() {+ cards.forEach(card => {+ let ramdomPos = Math.floor(Math.random() * 12);+ card.style.order = ramdomPos;+ });+ })();

cards.forEach(card => card.addEventListener('click', flipCard));
