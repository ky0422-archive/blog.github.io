# Default 트레잇

`Default`로 구조체, 열거형 타입 등에서 기본 값을 가져올 수 있습니다:

```rust
let (a, b, c, d): (usize, bool, String, Vec<i32>) = Default::default();

assert_eq!(a, 0);
assert_eq!(b, false);
assert_eq!(c, "");
assert_eq!(d, vec![]);
```

`Default` 트레잇을 구현하면 됩니다:

```rust
#[derive(Debug)]
struct Foo {
    x: i32,
    y: i32,
}

impl Default for Foo {
    fn default() -> Self {
        Foo { x: 0, y: 0 }
    }
}

fn main() {
    let foo = Foo::default();
    let foo: Foo = Default::default();

    assert_eq!(foo.x, 0);
    assert_eq!(foo.y, 0);
}
```

이렇게 구현된 `Default`는 `..`을 사용하여, 구현하지 않은 필드를 기본 값으로 채워줄 수 있습니다:

```rust
Foo { x: 1, ..Foo::default() };
Foo { x: 1, ..Default::default() };
```

`<Default를 구현한 타입>::default()`, `Default::default()` 모두 같은 역할입니다.
단, `Default::default()`의 경우엔 위 코드처럼 타입 어노테이션을 붙여줘 하는 경우도 있습니다.

## 열거형에서 Default

열거형(`enum`)의 경우엔 `Default` 트레잇 구현 없이 `#[default]` 속성(`attributes`)을 사용해 기본 값을 지정할 수 있습니다:

```rust
#[derive(Default, Debug)]
enum Foo {
    A,
    #[default]
    B,
}

fn main() {
    println!("{:?}", Foo::default());
}
```

단, 빈 아이템만 가능합니다. `B(String)` 같은 건 안된다는 소리죠. (내부적으로 `Default` 트레잇을 구현하기 때문에 불가능)

열거형의 아이템이 일급객체가 아니여서, 빈 아이템이 아니라면 `Default`를 적용하지 못한다고는 하지만, 개인적인 생각이긴하나 `Default` 매크로를 좀 건들면 해결될 문제라 생각합니다.
