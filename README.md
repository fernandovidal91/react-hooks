# useState

```
const [counter, setCounter] = useState(0);

function handlePlus() {
  setCounter((prevState) => prevState + 1);
}

function handleMinus() {
  setCounter((prevState) => prevState - 1);
}
```

# useEffect

```
// Executa toda vez que o componente é montado em tela.

useEffect(() => {
  console.log('Rodou')
})
```

```
// Executa somente uma vez quando o componente é montado em tela.

useEffect(() => {
  console.log('Rodou')
}, [])
```

```
// Executa toda vez que valor das variaveis name ou lastname sofrerem alterações em seu valor.

useEffect(() => {
  (async () => {
    await api.get();
  })();
}, [name, lastname])
```
OBS: Toda variável que for usada dentro do useEffect deve estar dentro de seu array.

```
// Executa uma função quando o componente for desmontado da tela.

useEffect(() => {
  return () => {
    // Função a ser executada
  }
}, [])
```


# useContext

```
import { useState, createContext, useContext } from "react";

const ThemeContext = createContext();

export default function UseContext() {
  const [mode, setMode] = useState('light');

  function handleTheme() {
    setMode((prevState) => (
      prevState === 'light'
        ? 'dark'
        : 'light'
    ));
  }

  const darkMode = {
    background: 'black',
    color: 'white',
  }

  const lightMode = {
    background: 'white',
    color: 'black',
  }

  return (
    <>
      <ThemeContext.Provider value={{ mode }}>
        <button
          onClick={handleTheme}
          style={mode === 'dark' ? darkMode : lightMode}
        >
          Mudar Tema
        </button>
        <Theme />
      </ThemeContext.Provider>
    </>
  );
}

function Theme() {
  const { mode } = useContext(ThemeContext);

  return (
    <>
      <p>Tema atual: <b>{mode}</b></p>
    </>
  )
}
```





