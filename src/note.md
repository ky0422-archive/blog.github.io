해당 문서의 일부는 [ky0422 티스토리 블로그](http://ky0422.tistory.com/)의 일부 글을 옮겨왔습니다.

---

모든 컨텐츠는 [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/) 라이센스를 따릅니다.

---

빠른 이해를 돕기 위해, 상황에 따라 일부 코드를 생략합니다. 예를 들어 아래와 같은 코드는

```rust
#[derive(Debug)]
struct Foo(i32, i32);

fn main() {
    println!("{:?}", Foo(1, 2));
}
```

```rust
// 생략

println!("{:?}", Foo(1, 2));
```

등으로 표시할 수 있습니다.
