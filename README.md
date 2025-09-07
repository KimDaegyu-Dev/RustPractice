# RustPractice

좋은 질문이에요 👍 Rust로 코딩테스트(Problem Solving) 준비할 때, **언어의 기초적인 문법**은 이미 익혔다고 하셨으니 이제는 **표준 라이브러리에서 자주 쓰이는 자료구조와 기능들**을 확실히 잡는 게 중요합니다. Rust는 C++이나 Java처럼 거대한 표준 라이브러리를 갖고 있진 않지만, **기본 컬렉션과 크레이트만 잘 써도 충분히 문제 풀이가 가능합니다.**

---

## 🔑 주요 컬렉션 (std::collections)

Rust 표준 라이브러리의 핵심 컨테이너들은 다음과 같아요:

* **Vec<T>**

  * 동적 배열. 코테에서 가장 많이 쓰이는 기본 자료구조.
  * `push`, `pop`, `sort`, `binary_search` 자주 활용.
  * 슬라이스(`&[T]`)와 함께 범위 접근이 빠르고 편리.

* **VecDeque<T>**

  * 양쪽에서 push/pop이 가능한 큐/덱. BFS, 슬라이딩 윈도우 문제에 필수.

* **HashMap\<K, V>**

  * 해시맵 (unordered\_map 같은 느낌).
  * 문자열 카운팅, frequency table, 그래프 adjacency list 등에 활용.
  * 기본 해시는 안전성을 위해 느릴 수 있어, 코테에서는 `hashbrown::HashMap` 같은 크레이트를 쓰기도 함.

* **BTreeMap\<K, V> / BTreeSet<T>**

  * 정렬 기반 맵/셋.
  * C++의 `map`, `set`과 유사.
  * 순서가 중요한 경우(예: lower\_bound, upper\_bound) 자주 씀.

* **HashSet<T>**

  * 중복 없는 원소 집합. membership check 용도로 많이 활용.

---

## 📚 기본 모듈 & 기능

* **std::cmp**: `min`, `max`, `Ordering`
* **std::collections::BinaryHeap**: 우선순위 큐 (기본은 max-heap, min-heap은 `Reverse` 래핑해서 사용).
* **std::iter / std::slice**: 반복자, 슬라이싱 유틸 (map, filter, enumerate 등).
* **std::string::String / \&str**: 문자열 처리. `split_whitespace()`, `chars()`, `bytes()` 자주 씀.
* **std::io**: 빠른 입력 처리를 위해 `stdin().read_line` 대신 버퍼링된 방식으로 구현 필요.

---

## 🛠️ 외부 크레이트 (코테에서 유용한 것들)

대부분의 온라인 저지에서 `Cargo.toml`을 마음대로 쓸 수 없지만, 허용되는 경우라면 다음이 유용합니다:

* **itertools**

  * 반복자 확장: `permutations`, `combinations`, `tuple_combinations`, `iproduct!` 등.
  * Python의 itertools 같은 편리함 제공.

* **regex**

  * 정규표현식 문제에서 편리.

* **num / num-bigint**

  * 큰 수 연산, 모듈러 연산 등이 필요할 때.

* **proconio / text\_io**

  * 빠른 입력 파싱용. (특히 AtCoder Rust 환경에서 많이 사용됨)

---

## 🚀 코테 준비 팁 (Rust 관점)

1. **입출력 최적화 필수**

   * `std::io::stdin().read_to_string` + `split_whitespace()`로 입력 한 번에 받고 파싱.
   * `println!`보다 `writeln!(buf, ...)` 식으로 버퍼 출력 후 한 번에 flush.

2. **패턴 매칭 적극 활용**

   * `match`, `if let`, `while let` → C++보다 훨씬 깔끔하게 상태 분기 가능.

3. **소유권/빌림 패턴 익숙해지기**

   * Vec이나 HashMap 다룰 때 `&`, `&mut`, `clone` 실수 줄이는 게 중요.

4. **알고리즘 구현 연습**

   * DFS/BFS, Dijkstra, Union-Find, Segment Tree, DP를 Rust로 직접 짜보는 게 필수.
   * 특히 `Rc<RefCell<T>>` 같은 걸 안 쓰고도 안전하게 구현하는 습관이 좋아요.

---

