# Step 1 - Styled Components

After creating a cool looking card we need to populate it with real time data instead of static data.

## 🥇 Goal

- Retrieve a list of Pokemon Data and have it be displayed through the PokeCard that we created. We will do this with fetch and ES6 promises to get data from the Poke Api and save it in the app's state.

## 🎬 Concepts

- Making calls with `useEffect`
- Using promises with `async/await`
- Managing state with `useState`

## 📚 Tasks

Import the `loadPokemon` helper function and the `useEffect` and `useState` functions from React. Afterwards call `loadPokemon()` in `useEffect`. `useEffect` is called whenever the component gets rendered on the page:

```javascript
import React, { useState, useEffect } from 'react'
import { getBackgroundType, getType, loadPokemon } from 'helper/pokemonHelpers';

const App = () => {
  const name = 'Bryan Wong';

  useEffect(() => {
    const fetcPokemon = async () => {
        try {
            const pokemonResults = await loadPokemon();
        } catch (err) {
            console.error(err);
        }
    }
    fetchResults();
  }, [])

  return (
    <StyledContainer className='site-card-wrapper'>
      <h1>Hi there, my name is {name}! Welcome to my Pokedex!</h1>
      <p>Hi Im a paragraph in React</p>
      <Row>
        <Col span={8}>
          <StyledCard typeName={getBackgroundType('grass')}>
            <Space align='start'>
              <div>
                <StyledTitle>Bulbasaur</StyledTitle>
                <StyledButton
                  typeName={getType('grass')}
                  width={'100'}
                  shape='round'
                  size='small'
                >
                  Grass
                </StyledButton>
                <StyledButton
                  typeName={getType('poison')}
                  width={'100'}
                  shape='round'
                  size='small'
                >
                  Poison
                </StyledButton>
              </div>
              <StyledImage alt='' src={getPokemonImage('1')} />
            </Space>
          </StyledCard>
        </Col>
      </Row>
    </StyledContainer>
  );
```

Check the Network panel of your Developer Tools to see that it is making an API call.

In order to render the Pokemon data and images, we need to store the results in state, using `useState`. State is where you can store values that belong to a component. Whenever the state changes, the component will re-render:

```javascript
const App = () => {
  const [pokemon, setPokemon] = useState([]);
  const name = 'Bryan Wong';

  useEffect(() => {
    const fetcPokemon = async () => {
      try {
          const pokemonResults = await loadPokemon();
          setPokemon(pokemonResults);
      } catch (err) {
          console.error(err);
      }
    }
    fetchResults();
  }, [])

  return (
    <StyledContainer className='site-card-wrapper'>
      <h1>Hi there, my name is {name}! Welcome to my Pokedex!</h1>
      <p>Hi Im a paragraph in React</p>
      <Row>
        <Col span={8}>
          <StyledCard typeName={getBackgroundType('grass')}>
            <Space align='start'>
              <div>
                <StyledTitle>Bulbasaur</StyledTitle>
                <StyledButton
                  typeName={getType('grass')}
                  width={'100'}
                  shape='round'
                  size='small'
                >
                  Grass
                </StyledButton>
                <StyledButton
                  typeName={getType('poison')}
                  width={'100'}
                  shape='round'
                  size='small'
                >
                  Poison
                </StyledButton>
              </div>
              <StyledImage alt='' src={getPokemonImage('1')} />
            </Space>
          </StyledCard>
        </Col>
      </Row>
    </StyledContainer>
  );
```