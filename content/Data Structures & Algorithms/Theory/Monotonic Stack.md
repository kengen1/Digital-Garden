*A monotonic stack is a stack that always maintains a specific order*

- **Monotonic Increasing Stack**: Elements are in increasing order (top element is the smallest)
- **Monotonic Decreasing Stack**: Elements are in decreasing order (top element is the largest)

Unlike a regular stack, a monotonic stack removes elements when the order is violated, ensuring that every element is processed in an efficient manner.


### Algorithm
*Whenever a new element is added, previous elements that violate the order are popped*

- Initialize an empty stack.
- Iterate through the elements and for each element:
    - while stack is not empty AND top of stack is more than the current element
        - pop element from the stack
    - Push the current element onto the stack.
- At the end of the iteration, the stack will contain the monotonic increasing order of elements.

### Code Implementation

```cpp

vector<int> monotonicIncreasing(vector<int>& nums)
{
    int n = nums.size();
    stack<int> st;
    vector<int> result;

    // Traverse the array
    for (int i = 0; i < n; ++i) {

        // While stack is not empty AND top of stack is more
        // than the current element
        while (!st.empty() && st.top() > nums[i]) {

            // Pop the top element from the
            // stack
            st.pop();
        }

        // Push the current element into the stack
        st.push(nums[i]);
    }

    // Construct the result array from the stack
    while (!st.empty()) {
        result.insert(result.begin(), st.top());
        st.pop();
    }

    return result;
}

```