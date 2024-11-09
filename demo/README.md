![Banner](./../images/banner.png)

# PROYECTO 2: Demo

## Planteamiento

La demo consiste en desarrollar un cuestionario interactivo de selección múltiple en JavaScript. Los usuarios deben poder responder a una serie de preguntas con varias opciones de respuesta. Una vez que el usuario responda a una pregunta, el programa debe proporcionar retroalimentación inmediata, indicando si la respuesta fue correcta o incorrecta. Además, si la respuesta fue incorrecta, el programa debe proporcionar la respuesta correcta.

El cuestionario debe estar diseñado de manera que las preguntas y respuestas se almacenen en una estructura de datos, permitiendo la flexibilidad para agregar, eliminar o cambiar preguntas con facilidad.

Se implementará utilizando dos enfoques: la programación orientada a objetos (POO) y la programación funcional (PF). En la versión de POO, las preguntas se modelarán como objetos de una clase `Question`, y el cuestionario se modelará como un objeto de una clase `Quiz`. En la versión de PF, las preguntas serán objetos literales almacenados en un `array`, y las funciones se utilizarán para procesar las preguntas y respuestas.

## Requerimientos

- Permitir a los usuarios responder preguntas con opciones de respuesta.
- Proporcionar retroalimentación inmediata sobre las respuestas de los usuarios.
- Almacenar los datos de las preguntas y las respuestas en una variable.
- Implementar la solución utilizando programación orientada a objetos (POO) y programación funcional (PF).

## Solución explicada paso a paso (POO)

**1. Crea la clase `Question`**

Esta clase representará una sola pregunta. Tendrá las propiedades `question`, `options`, `correctAnswer` y `userAnswer`, y un método `isCorrectAnswer()` que determina si la respuesta del usuario es correcta.


```javascript
class Question {
  constructor(question, options, correctAnswer, userAnswer) {
    this.question = question;
    this.options = options;
    this.correctAnswer = correctAnswer;
    this.userAnswer = userAnswer;
  }

  isCorrectAnswer() {
    return this.userAnswer === this.correctAnswer;
  }
}
```

**2. Crea la clase `Quiz`**

Esta clase representará el cuestionario completo. Contendrá un array de objetos Question y un método askQuestions() que recorrerá cada pregunta, imprimirá la pregunta y la respuesta del usuario, y dirá si la respuesta es correcta.

```javascript
class Quiz {
  constructor(questions) {
    this.questions = questions;
  }

  askQuestions() {
    this.questions.forEach((question) => {
      console.log(question.question);
      const userAnswer = question.userAnswer;
      if (question.isCorrectAnswer()) {
        console.log("¡Correcto!");
      } else {
        console.log(`Incorrecto. La respuesta correcta es ${question.correctAnswer}`);
      }
    });
  }
}

```

**3. Crea instancias de las clases y corre el cuestionario**

Finalmente, crea instancias de la clase Question para cada pregunta en tu cuestionario, y luego crea una instancia de la clase Quiz con esas preguntas. Luego, llama al método askQuestions() en la instancia del cuestionario para empezar a hacer las preguntas.

```javascript
const questions = [
  new Question("¿Cuál es la capital de Francia?", ["París", "Londres", "Roma"], "París", "París"),
  new Question("¿Cuál es la capital de Inglaterra?", ["Madrid", "Londres", "Berlín"], "Londres", "Berlín"),
  new Question("¿Cuál es la capital de España?", ["Madrid", "Barcelona", "Sevilla"], "Madrid", "Madrid"),
  new Question("¿Cuál es la capital de Italia?", ["Milán", "Roma", "Nápoles"], "Roma", "Milán"),
  new Question("¿Cuál es la capital de Alemania?", ["Hamburgo", "Berlín", "Múnich"], "Berlín", "Berlín"),
  new Question("¿Cuál es la capital de Rusia?", ["Moscú", "San Petersburgo", "Sochi"], "Moscú", "San Petersburgo"),
  new Question("¿Cuál es la capital de Japón?", ["Osaka", "Tokio", "Yokohama"], "Tokio", "Tokio"),
  new Question("¿Cuál es la capital de Australia?", ["Sydney", "Melbourne", "Canberra"], "Canberra", "Sydney"),
];

const quiz = new Quiz(questions);
quiz.askQuestions();

```

Este es el código completo:

```javascript
class Question {
  constructor(question, options, correctAnswer, userAnswer) {
    this.question = question;
    this.options = options;
    this.correctAnswer = correctAnswer;
    this.userAnswer = userAnswer;
  }

  isCorrectAnswer() {
    return this.userAnswer === this.correctAnswer;
  }
}

class Quiz {
  constructor(questions) {
    this.questions = questions;
  }

  askQuestions() {
    this.questions.forEach((question) => {
      console.log(question.question);
      const userAnswer = question.userAnswer;
      if (question.isCorrectAnswer()) {
        console.log("¡Correcto!");
      } else {
        console.log(`Incorrecto. La respuesta correcta es ${question.correctAnswer}`);
      }
    });
  }
}

const questions = [
  new Question("¿Cuál es la capital de Francia?", ["París", "Londres", "Roma"], "París", "París"),
  new Question("¿Cuál es la capital de Inglaterra?", ["Madrid", "Londres", "Berlín"], "Londres", "Berlín"),
  new Question("¿Cuál es la capital de España?", ["Madrid", "Barcelona", "Sevilla"], "Madrid", "Madrid"),
  new Question("¿Cuál es la capital de Italia?", ["Milán", "Roma", "Nápoles"], "Roma", "Milán"),
  new Question("¿Cuál es la capital de Alemania?", ["Hamburgo", "Berlín", "Múnich"], "Berlín", "Berlín"),
  new Question("¿Cuál es la capital de Rusia?", ["Moscú", "San Petersburgo", "Sochi"], "Moscú", "San Petersburgo"),
  new Question("¿Cuál es la capital de Japón?", ["Osaka", "Tokio", "Yokohama"], "Tokio", "Tokio"),
  new Question("¿Cuál es la capital de Australia?", ["Sydney", "Melbourne", "Canberra"], "Canberra", "Sydney"),
];

const quiz = new Quiz(questions);
quiz.askQuestions();

```



## Solución explicada paso a paso (PF)

**1. Define una estructura de datos para las preguntas y las respuestas usando objetos literales.**

Primero, necesitamos un lugar para almacenar todas nuestras preguntas, opciones de respuesta y respuestas correctas. Para esto, creamos un `array` llamado `questions`. 

Cada pregunta es un objeto con cuatro propiedades: `question` (la pregunta misma), `options` (un `array` con las opciones de respuesta), `correctAnswer` (la respuesta correcta a la pregunta) y `userAnswer` (la respuesta proporcionada por el usuario).


```javascript
const questions = [
  {
    question: "¿Cuál es la capital de Francia?",
    options: ["París", "Londres", "Roma"],
    correctAnswer: "París",
    userAnswer: "París" // Respuesta correcta
  },
  {
    question: "¿Cuál es la capital de Inglaterra?",
    options: ["Madrid", "Londres", "Berlín"],
    correctAnswer: "Londres",
    userAnswer: "Berlín" // Respuesta incorrecta
  },
  {
    question: "¿Cuál es la capital de España?",
    options: ["Madrid", "Barcelona", "Sevilla"],
    correctAnswer: "Madrid",
    userAnswer: "Madrid" // Respuesta correcta
  },
  {
    question: "¿Cuál es la capital de Italia?",
    options: ["Milán", "Roma", "Nápoles"],
    correctAnswer: "Roma",
    userAnswer: "Milán" // Respuesta incorrecta
  },
  {
    question: "¿Cuál es la capital de Alemania?",
    options: ["Hamburgo", "Berlín", "Múnich"],
    correctAnswer: "Berlín",
    userAnswer: "Berlín" // Respuesta correcta
  },
  {
    question: "¿Cuál es la capital de Rusia?",
    options: ["Moscú", "San Petersburgo", "Sochi"],
    correctAnswer: "Moscú",
    userAnswer: "San Petersburgo" // Respuesta incorrecta
  },
  {
    question: "¿Cuál es la capital de Japón?",
    options: ["Osaka", "Tokio", "Yokohama"],
    correctAnswer: "Tokio",
    userAnswer: "Tokio" // Respuesta correcta
  },
  {
    question: "¿Cuál es la capital de Australia?",
    options: ["Sydney", "Melbourne", "Canberra"],
    correctAnswer: "Canberra",
    userAnswer: "Sydney" // Respuesta incorrecta
  }
];

```



**2. Crear la función isCorrectAnswer**

La función `isCorrectAnswer` toma dos parámetros: el objeto `question` y una `answer` (respuesta). Esta función compara la answer con la respuesta correcta de la pregunta (accedida como question.correctAnswer). Si son iguales, devuelve true; de lo contrario, devuelve false. Esta función nos ayuda a determinar si una respuesta dada es correcta o no.

```javascript
function isCorrectAnswer(question, answer) {
  return answer === question.correctAnswer;
}
```


**3. Definir la función getUserAnswer**

En tu ejemplo, parece haber una confusión en esta parte. La función `getUserAnswer` que proporcionas selecciona una respuesta de manera aleatoria de las opciones disponibles. Sin embargo, en base a tu arreglo de preguntas, parece que quieres que el usuario proporcione respuestas específicas (algunas correctas y algunas incorrectas). En este caso, podríamos cambiar la función `getUserAnswer` para que simplemente devuelva la respuesta del usuario proporcionada en el objeto de la pregunta.

```javascript
function getUserAnswer(question) {
  // Esta función devuelve la respuesta proporcionada por el usuario
  return question.userAnswer;
}

```


**4. Crear la función askQuestion**

La función askQuestion toma como parámetro un objeto question. Primero, imprime la pregunta (accedida como question.question). Luego, obtiene la respuesta del usuario llamando a la función getUserAnswer. Si la respuesta del usuario es correcta (determinada por la función isCorrectAnswer), imprime "¡Correcto!". Si la respuesta del usuario es incorrecta, imprime "Incorrecto" junto con la respuesta correcta.

```javascript
function askQuestion(question) {
  console.log(question.question);
  const userAnswer = getUserAnswer(question); 
  if (isCorrectAnswer(question, userAnswer)) {
    console.log("¡Correcto!");
  } else {
    console.log("Incorrecto. La respuesta correcta es " + question.correctAnswer);
  }
}
```


**5. Utilizar la función askQuestion para cada pregunta**

Finalmente, queremos hacer todas las preguntas de nuestro array questions. Para esto, usamos el método forEach de JavaScript, que ejecuta una función para cada elemento en un array. Pasamos la función askQuestion a forEach, de modo que para cada objeto question en questions, la función askQuestion se ejecutará con ese objeto como argumento.


```javascript
questions.forEach((question) => {
  askQuestion(question);
});

```


Este es el código completo:

```javascript
// Paso 1: Definir la estructura de datos para las preguntas y las respuestas
const questions = [
  {
    question: "¿Cuál es la capital de Francia?",
    options: ["París", "Londres", "Roma"],
    correctAnswer: "París",
    userAnswer: "París" // Respuesta correcta
  },
  {
    question: "¿Cuál es la capital de Inglaterra?",
    options: ["Madrid", "Londres", "Berlín"],
    correctAnswer: "Londres",
    userAnswer: "Berlín" // Respuesta incorrecta
  },
  {
    question: "¿Cuál es la capital de España?",
    options: ["Madrid", "Barcelona", "Sevilla"],
    correctAnswer: "Madrid",
    userAnswer: "Madrid" // Respuesta correcta
  },
  {
    question: "¿Cuál es la capital de Italia?",
    options: ["Milán", "Roma", "Nápoles"],
    correctAnswer: "Roma",
    userAnswer: "Milán" // Respuesta incorrecta
  },
  {
    question: "¿Cuál es la capital de Alemania?",
    options: ["Hamburgo", "Berlín", "Múnich"],
    correctAnswer: "Berlín",
    userAnswer: "Berlín" // Respuesta correcta
  },
  {
    question: "¿Cuál es la capital de Rusia?",
    options: ["Moscú", "San Petersburgo", "Sochi"],
    correctAnswer: "Moscú",
    userAnswer: "San Petersburgo" // Respuesta incorrecta
  },
  {
    question: "¿Cuál es la capital de Japón?",
    options: ["Osaka", "Tokio", "Yokohama"],
    correctAnswer: "Tokio",
    userAnswer: "Tokio" // Respuesta correcta
  },
  {
    question: "¿Cuál es la capital de Australia?",
    options: ["Sydney", "Melbourne", "Canberra"],
    correctAnswer: "Canberra",
    userAnswer: "Sydney" // Respuesta incorrecta
  }
];


// Paso 2: Crear la función isCorrectAnswer
function isCorrectAnswer(question, answer) {
  return answer === question.correctAnswer;
}

// Paso 3: Definir la función getUserAnswer
function getUserAnswer(question) {
  // Esta función devuelve la respuesta proporcionada por el usuario
  return question.userAnswer;
}


// Paso 4: Crear la función askQuestion
function askQuestion(question) {
  console.log(question.question);
  const userAnswer = getUserAnswer(question); 
  if (isCorrectAnswer(question, userAnswer)) {
    console.log("¡Correcto!");
  } else {
    console.log("Incorrecto. La respuesta correcta es " + question.correctAnswer);
  }
}

// Paso 5: Utilizar la función askQuestion para cada pregunta
questions.forEach((question) => {
  askQuestion(question);
});

```