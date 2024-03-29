# Hooks의 개념과 useState, useEffect
Hook을 사용하면 함수 컴포넌트도 클래스 컴포넌트의 기능을 모두 동일하게 구현할 수 있음

hook의 이름은 모두 use로 시작

## useState()
가장 많이 사용되는 hook으로 state를 사용하기 위한 hook입니다.
➡️ 함수 컴포넌트에서는 state를 제공하지 않기 떄문입니다.

### useState() 사용법
```JavaScript
const [변수명, set변수명] = useState(초기값);
```

## useEffect()
useEffect는 사이드 이팩트를 수행하기 위한 hook

리액트에서 사이드 이팩트는 서버에서 데이터를 받아오거나 수동으로 DOM을 변경하는 작업을 의미 <br>
이는 다른 컴포넌트에 영향을 미칠 수 있으며 렌더중에는 작업이 완료될수 없고 끝난 이후에 실행되는 작업<br>

```JavaScript
useEffect(이펙트 함수, 의존성 배열);
```
배열 안에 있는 변수 중 하나라도 변경되면 이펙트 함수가 호출됨<br>
이펙트 함수는 처음 컴포넌트가 렌더링된 후에 업데이트로 인한 재렌더링 후 실행된 <br>
의존성 배열을 생햑하면 컴포넌트가 업데이트 될 때마다 호출

```JavaScript
useEffect(() =>{
    // 컴포넌트가 마운트 된 이후,
    // 의존성 배열에 있는 변수들 중 하나라도 값이 변경되었을 때 실행됨
    // 의존성 배열에 빈 배열([])을 넣으면 마운트와 언마운트시에 단 한 번 씩만 실행됨
    // 의존성 배열 생략시 컴포넌트 없데이트 시마다 실행됨
    ...
    
    return () => {
        // 컴포넌트가 마운트 해제되기 전에 실행됨
        ...
    }

}, [의존성 변수1, 의존성 변수2, ...]);