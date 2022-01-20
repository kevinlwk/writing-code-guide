# writing-code-guide

### How to start a problem

1. Determine what your requirements are and WRITE THEM DOWN

2. Write what you know you DEFINITELY NEED

  - i.e. in recursion I definitely need:

```c
// determine what not only what my return/param types are (i.e. int)
//   but also what its meaning is (i.e. last_num, curr_num_so_far).

<return_type> funcy_name(<params>) {
  // do something here

  if (is_base_case(params)) {

    // return something? do something?

  } else {

    // now I know I'm definitely not in my base case... what assumptions can I make?
    // what do I know about my current state?
  }
}
```

3. Use lots of comments to guide your "later" steps

```c
int double_and_add(int a, int b) {
  int doubled_a = a * 2;
  // int doubled_b is an integer that has been doubled.
  
  return doubled_a + doubled_b;
}
```

Basically, when writing code, we want to "assume" that what we have written is correct so far. When writing function A, we work under the assumption function B is working.

If I want to write a sum function:

```c
int sum(int[] nums, int n) {
  int sum_so_far = 0;
  
  for (int i = 0; i < n; i++) {
    // assuming add works...
    sum_so_far = add(sum_so_far, nums[i]);
  }
  
  return sums_so_far;
}
```

I will simply assume that `add(int, int)` works and then write it/fix it later.

# Debugging Code?

1. Write your assumptions about each state of your code.
  - Make it very explicit (it'll help you notice things)
  - Talk out loud, translate your code to English and back to code.
  - Write out the possible values of each variable

2. Draw your stack frame. What do you know at each stage of the execution?

```c
int sum_to_(int curr_num) {
  if (curr_num != 0) {
    next_num = curr_num - 1;
    return sum_to_(next_num);
  }
}

int main(void) {
  int x = 2;
  return sum_to_(x);
}

/*
STACK TRACE
=========
sum_to_
  curr_num = 0
  
=========
sum_to_
  curr_num = 1
  next_num = 0
  
=========
sum_to_
  curr_num = 2
  next_num = 1
=========
main:
  x = 2
  
=========
END TRACE
*/
```

3. Use debug statements to check your assumptions!

4. Call your boyfriend!

# Lost and not sure what to do?

1. Check your assumptions. Revisit the question definition, see what about your function lines up.

2. Pseudocode your problem

3. Visit similar problems or try coding "simpler" versions of your problem to move in the right direction

4. Talk out loud

5. Still not working? Go for a walk LOL you're probably too tunnel visioned
