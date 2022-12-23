```
const dispatch = useDispatch()
```

Этот хук возвращает ссылку на функцию `dispatch` из Redux хранилища(store). Вы можете использовать его для отправки(dispatch) действий по мере необходимости.

Примеры

```
import React from 'react'  
import { useDispatch } from 'react-redux'  
  
export const CounterComponent = ({ value }) => {  
	const dispatch = useDispatch()  
	  
	return (  
		<div>  
			<span>{value}</span>  
			<button onClick={() => dispatch({ type: 'increment-counter' })}>  
				Increment counter  
			</button>  
		</div>  
	)  
}
```

При передаче колбэка с помощью `dispatch` дочернему компоненту вы иногда можете захотеть запомнить его с помощью [`useCallback`](https://reactjs.org/docs/hooks-reference.html#usecallback). _Если_ дочерний компонент пытается оптимизировать поведение рендеринга с помощью `React.memo()` или аналогичного, это позволяет избежать ненужного рендеринга дочерних компонентов из-за измененной ссылки колбэка.

```
import React, { useCallback } from 'react'  
import { useDispatch } from 'react-redux'  
  
export const CounterComponent = ({ value }) => {  
	const dispatch = useDispatch()  
	const incrementCounter = useCallback(  
			() => dispatch({ type: 'increment-counter' }),  
			[dispatch]  
		)  
		  
		return (  
			<div>  
				<span>{value}</span>  
				<MyIncrementButton onIncrement={incrementCounter} />  
			</div>  
		)  
}  
  
export const MyIncrementButton = React.memo(({ onIncrement }) => (  
<button onClick={onIncrement}>Increment counter</button>  
))
```

Ссылка на функцию `dispatch` будет стабильной до тех пор, пока один и тот же экземпляр хранилища(store) передается в `<Provider>`. Обычно этот экземпляр хранилища(store) никогда не изменяется в приложении.

Тем не менее, линтер React не знает об особенности `dispatch` быть стабильным, и предупредит, что переменная `dispatch` должна быть добавлена в массивы зависимостей для `useEffect` и `useCallback`. Самое простое решение - добавить их:

```
export const Todos = () => {  
	const dispatch = useDispatch()  
	  
	useEffect(() => {  
		dispatch(fetchTodos())  
		// Безопасно добавляем dispatch в массив зависимостей  
	}, [dispatch])  
}
```
#redux