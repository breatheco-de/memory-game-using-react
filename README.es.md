<!-- hide -->
# ¡Construye un Juego de Memoria con React: Encuentra los Pares!
<!-- endhide -->

<how-to-start>

## 🌱 ¿Cómo iniciar este proyecto?

No clones este repositorio porque vamos a utilizar una plantilla diferente.

Recomendamos abrir la `plantilla de React` utilizando una herramienta de aprovisionamiento como [Codespaces](https://4geeks.com/lesson/what-is-github-codespaces) (recomendado) o [Gitpod](https://4geeks.com/lesson/how-to-use-gitpod). Alternativamente, puedes [clonar el repositorio de GitHub](https://4geeks.com/how-to/github-clone-repository) en tu computadora local usando el comando `git clone`.

Este es el repositorio que necesitas abrir o clonar:

```
https://github.com/4GeeksAcademy/react-hello
```

> ⚠ ¡Necesitarás tener Node.js instalado si lo haces localmente, pero todo eso ya está instalado en Codespaces o Gitpod!

</how-to-start>

## 📝 Instrucciones

### Paso 1: Configura el Proyecto

- [ ] Configura el proyecto boilerplate desde la plantilla de React proporcionada.
  
- [ ] Sigue las instrucciones en el README del repositorio para configurar tu entorno de desarrollo.

### Paso 2: Planifica la Estructura del Juego

- [ ] Crea un boceto o diagrama de cómo será la estructura de tu juego de memoria.
  - ¿Cuántas cartas habrá?
  - ¿Cómo representarás las cartas en el estado?
  - ¿Qué propiedades necesitarás para cada carta (por ejemplo, id, imagen, estado volteado)?

### Paso 3: Implementa el Tablero de Juego

- [ ] Crea un componente `Board` que contendrá las cartas.

- [ ] Crea un componente `Card` que representará cada carta individual.

- [ ] Genera un conjunto de cartas con pares iguales y barájalas aleatoriamente.

```jsx
// Ejemplo de generación de cartas
const cards = [
  { id: 1, image: 'url1', matched: false },
  { id: 2, image: 'url2', matched: false },
  // ... más cartas
];
```

### Paso 4: Maneja el Estado de las Cartas con useState

- [ ] Utiliza el hook `useState` para manejar el estado de las cartas en el componente `Board`.
- [ ] Crea estados para:
  - Las cartas volteadas actualmente.
  - Las cartas que han sido encontradas (pares correctos).
  - El número de intentos o movimientos realizados (opcional).

```jsx
const [cards, setCards] = useState([]);
const [flippedCards, setFlippedCards] = useState([]);
const [matchedCards, setMatchedCards] = useState([]);
```

### Paso 5: Implementa la Lógica del Juego con useEffect

- [ ] Utiliza el hook `useEffect` para verificar si las dos cartas volteadas son un par.

- [ ] Si las cartas coinciden, actualiza el estado para reflejar que han sido encontradas.

- [ ] Si no coinciden, voltea las cartas de nuevo después de un breve retraso.

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

### Paso 6: Agrega Control de Eventos de Clic

- [ ] En el componente `Card`, agrega un evento `onClick` que maneje cuando una carta es seleccionada.

- [ ] ¡Asegúrate de que no puedas voltear más de dos cartas a la vez y que no puedas seleccionar la misma carta dos veces!

```jsx
const handleCardClick = (card) => {
  if (flippedCards.length < 2 && !flippedCards.includes(card)) {
    setFlippedCards([...flippedCards, card]);
  }
};
```

### Paso 7: Agrega Animaciones Simples

- [ ] Utiliza CSS para agregar transiciones o animaciones cuando las cartas se voltean.

- [ ] Puedes cambiar la clase CSS de la carta según su estado (volteada o no) y aplicar estilos en consecuencia.

```css
.card {
  transition: transform 0.6s;
  transform-style: preserve-3d;
}

.card.flipped {
  transform: rotateY(180deg);
}
```

### Paso 8: Mejora la Interfaz de Usuario

- [ ] ¡Agrega elementos visuales como un contador de movimientos o un temporizador!

- [ ] Asegúrate de que el juego sea responsivo y se vea bien en diferentes tamaños de pantalla.

## Sección de Bonus

### Características Adicionales para Practicar y Mejorar el Proyecto

1. **Contador de Puntuación:** ¡Implementa un sistema de puntuación basado en el número de movimientos o el tiempo que tarda el jugador en completar el juego!

2. **Niveles de Dificultad:** Agrega diferentes niveles de dificultad con más o menos cartas.

3. **Sonidos y Efectos:** ¡Añade efectos de sonido al voltear cartas o encontrar un par!

4. **Guardar Progreso:** Permite al jugador pausar y continuar el juego guardando el estado en el almacenamiento local.

5. **Tema Personalizable:** ¡Deja que el jugador elija entre diferentes temas o conjuntos de imágenes para las cartas!

6. **Juego Multijugador:** Implementa un modo para que dos jugadores compitan por turnos y registra quién encuentra más pares.

¡Explora diferentes mejoras para hacer tu juego de memoria más interactivo y entretenido!
