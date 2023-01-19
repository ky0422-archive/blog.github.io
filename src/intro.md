# 들어가기 앞서

해당 Book은 Rust (러스트) 프로그래밍 언어의 중급 이상의 내용을 다루는 문서입니다. 이 Book은 가이드가 아닌, 참고 문서입니다. (각 문서는 별개임.)

Rust를 처음 접하는 분들은 [Rust Book](https://doc.rust-lang.org/book/) ([한국어 번역](https://rinthel.github.io/rust-lang-book-ko/))을 먼저 읽어보시기 바랍니다.

목차는 크게 `Beginner` (초급), `Intermediate` (중급), `Advanced` (고급)으로 나뉘어져 있습니다. `Beginner`는 비교적 쉬운 내용을 다루고 있으며, `Intermediate` 및 `Advanced`는 Rust의 기본적인 내용을 이해하고 있는 분들을 대상으로 합니다.
또한, `Advanced`는 CS (Computer Science)의 기본적인 내용을 이해하고 있는 분들을 대상으로 합니다.

`Let's write!`는 무언가를 만들어보는 과정입니다. 코드를 복사해도 되지만, 직접 작성해보는 것을 권장합니다.

# 목차

-   [Beginner](./beginner/README.md)
    -   [클로저(`closure`)의 정체성](./beginner/closure.md)
    -   [`constant` (상수)와 `const fn`](./beginner/const.md)
    -   [`Default` 트레잇](./beginner/default.md)
    -   [`Cow<T>` 타입](./beginner/cow.md)
    -   [`Hash` 트레잇, `Hasher`, `DefaultHasher`](./beginner/hash.md)
    -   [`From`, `TryFrom` (Feat. `Into`, `TryInto`)](./beginner/from.md)
    -   [`#[inline]` 속성](./beginner/inline.md)
    -   [`&'static T`와 `T: 'static`의 차이점](./beginner/static.md)
-   [Intermediate](./intermediate/README.md)
    -   [함수 오버로딩 구현하기](./intermediate/overloading.md)
    -   [모나드 `bind` 함수 구현하기](./intermediate/bind.md)
    -   [`?Trait` 바운드와 marker 타입](./intermediate/marker.md)
    -   [`Any` 트레잇과 `TypeId`](./intermediate/any.md)
    -   [절차적 매크로, `syn`, `quote`, `Attribute` 만들기](./intermediate/macro.md)
    -   [`for<'a>` (상위 트레잇 바운드 `HRTB`)](./intermediate/for.md)
-   [Advanced](./advanced/README.md)
    -   [`Pin`과 `Unpin`](./advanced/pin.md)
    -   [`RwLock`, 그리고 `Mutex`의 차이점](./advanced/rwlock.md)
    -   [`atomic` 타입과 `Ordering` 열거형 (feat. CPU 명령어 처리)](./advanced/atomic.md)
    -   [`repr` 속성 (feat. 메모리 정렬)](./advanced/repr.md)
-   [Let's write!](./lets_write/README.md)
    -   [`Any` 트레잇을 사용해서 `JSON` 비스무리한 매크로 만들기](./lets_write/json.md)
-   [번외](./etc/README.md)
    -   [Rust가 C++를 대체할 수 있을까?](./etc/rust_vs_cpp.md)
-   [비고](./note.md)
