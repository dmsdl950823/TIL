# localStorage & sessionStorage

||localStorage|sessionStorage|
|------|---|---|
|공통점|저장공간으로 사용할 수 있음|테스트3|
|차이점|테스트2|세션이 종료되면 데이터도 함께 사라짐|


--------

## localStorage

1. ```setItem()``` : 특정 이름의 데이터 저장
```
  localStorage.test = '123';
  localStorage.setItem('test', '123')
```

2. ```getItem()``` : 특정 이름의 데이터 불러오기
```
  localStorage.getItem('test')
  localStorage.getItem()        // 전체 값 불러오기
```

3. ```removeItem()``` : 특정 이름의 데이터 삭제
```
  localStorage.removeItem('test')
  localStorage.clear()          // 전체 값 삭제
```

----------

## sessionStorage
세션을 기준으로 데이터가 저장 및 유지되기 때문에 이 객체에 저장된 값은 일시적인 수명을 가진다. <br>
만약 세션이 종료될 경우(브라우저를 닫거나 일정시간 아무런 동작이 없을경우) 저장된 값은 삭제된다.
<br>
데이터가 삭제되지 않길 바랄경우 localStorage를 사용하는 것이 좋다. <br>
메서드는 localStorage와 동일하게 갖는다.