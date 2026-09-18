# Trial II — *The Critique*

*Warden of the Foundations · Midterm 1 · 15 %*

This trial **requires** you to use an LLM. You will paste the prompt and the reply, then critique what you got. Reading and judging AI output is part of the job now; we are practicing it on purpose.

---

## The prompt

Open Claude (or your LLM of choice) and paste **this exact prompt**:

> *Write a C++ function template that returns the largest element of a `std::vector<T>`. Handle the case where the vector is empty. Briefly explain your design choices.*

Tell us which tool you used and the date:

- **Tool:** Claude
- **Date of the conversation:** 2026-09-17

---

## The LLM's reply

Paste the **full reply**, code and prose. Use a fenced code block for the code. Do not edit the reply — we want to see what you actually got.

```cpp
template <typename T>
std::optional<T> maxElement(const std::vector<T>& vec) {
    if (vec.empty()) {
        return std::nullopt;
    }

    T largest = vec[0];
    for (const auto& elem : vec) {
        if (elem > largest) {
            largest = elem;
        }
    }
    return largest;
}
```

Design choices
std::optional<T> for the return type: This is the core decision. An empty vector has no "largest element," so the function needs a way to express "no answer" without picking an arbitrary sentinel value (which wouldn't work generically anyway — what would you use for a std::string or a custom type?). std::optional makes the possibility of absence explicit in the type signature, forcing callers to handle it rather than silently getting garbage or undefined behavior.
Alternative considered — throwing an exception: You could instead throw std::invalid_argument("empty vector") on an empty input. This is reasonable too, and arguably better if an empty vector should be treated as a programmer error rather than a normal case to handle. I chose optional because "give me the max, or tell me there isn't one" feels like a query with a valid negative answer, not an exceptional circumstance — but either is defensible depending on your use case.
T requires operator< (via operator> here): Only comparison is required of T, not default-constructibility, arithmetic operations, or anything else. This keeps the template usable for any comparable type (ints, strings, custom classes with overloaded comparison operators, etc.).
Manual loop instead of std::max_element: I could've just wrapped std::max_element(vec.begin(), vec.end()) and checked against vec.end(). That's arguably more idiomatic C++. I wrote it out manually here mainly for clarity/pedagogy — in production code, prefer the standard algorithm:
Pass by const&: Avoids copying the entire vector; we only need to read it.

---

## My critique  *( ≥ 150 words )*

Your critique must read like an engineer reviewing a colleague's pull request — specific, technical, and naming exactly what the LLM did. A vague critique ("looks fine to me, but it could be better") is *not* full credit even if the LLM's code was great.

Address each of these:

- **Compile.** Did you actually try to compile and run the code? On what types? What happened?
- **Empty case.** What does the empty-vector case actually do in this code? Is the LLM's choice reasonable? Is it different from what *you* would have chosen?
- **Requirements on `T`.** What does the code require of `T`? What happens if you instantiate it with a type that doesn't support `<` (e.g., a custom struct)?
- **Const-correctness.** Pass by value or by reference? Return by value or by reference? Would you change either?
- **`std::max_element`?** Did the LLM cheat by using the algorithm header, or did it write the loop? Which would *you* have shipped, and why?
- **One concrete improvement.** Name one specific change you would make before merging this into a real project. Not "make it better" — a concrete code change.

Claude wrote some very good code, and effectively demonstrated it with an example of using vectors and simply finding the largest. I ran and compiled the code and it worked the first time! It printed out the largest integer in a vector I created, which was 9. In the case of an empty vector it simply prints out “Vector is empty”, which I would have changed to something else like, “There are no items in this vector”. Both get the point across. It wants the type to be int, but will work with other types. It uses pass by reference, which is the same way I would do it. It wrote the loop, but I think I would use the algorithm since it is shorter and probably faster. I think I would switch to the algorithm to improve this code. I would also make sure my naming convention is airtight and that I leave enough comments for other people to read.
