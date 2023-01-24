# 모나드 bind 함수 구현하기

먼저 모나드가 뭔지 모른다면, [구글링을 해보도록 합시다.](https://www.google.com/search?q=Monad&oq=Monad)  
금붕어도 이해할 만큼 쉽게 설명하면, `Option<T>`, `Result<T, E>` 같은게 모나드입니다.

자세한건 생략하겠지만, 물론 이게 모나드의 전부가 아닙니다.
사실 필자도 모나드에 대해서 자세하게 아는건 아닙니다.
이 글에선 모나드의 강력한 기능중 하나인 `bind` (하스켈에선 `>>=` 연산자) 를 구현해보고자 합니다.

러슬람들은 트레잇을 참 좋아합니다. 트레잇을 선언하고, 그 트레잇을 구현해봅시다:

```rust
pub trait Monad {
    type T;
    type U;

    fn bind<F>(self, f: F) -> Self::U
    where
        F: FnOnce(Self::T) -> Self::U;
}
```

`type T`는 `bind`의 인자가 받는 함수(`f`)의 인자이며, `type U`는 `bind`와 `f`의 반환값입니다.  
이렇게만 말하면 뭔말인지 이해가 힘드니, 직접 구현해보며 이해해봅시다:

```rust
impl<T> Monad for Option<T> {
    type T = T;
    type U = Option<T>;

    fn bind<F>(self, f: F) -> Self::U
    where
        F: FnOnce(Self::T) -> Self::U,
    {
        match self {
            Some(x) => f(x),
            None => None,
        }
    }
}
```

`Option<T>`에 대한 `Monad` 구현입니다. `bind` 함수를 봅시다.  
만약 `self` (`Option<T>`)가 `Some<T>` 이면, 함수 `f`를 실행하며, 아니라면 그냥 `None`을 반환합니다.

이제 한층 더 편한 러스트 프로그래밍을 할 수 있습니다:

```rust
assert_eq!(Some(10).bind(|x| Some(x * 10)), Some(100));
assert_eq!(None::<usize>.bind(|x| Some(x * 10)), None);

let (mul_5, div_10) = (|x: usize| Some(x * 5), |x: usize| Some(x / 10));

assert_eq!(Some(10).bind(mul_5).bind(div_10), Some(5));
```
