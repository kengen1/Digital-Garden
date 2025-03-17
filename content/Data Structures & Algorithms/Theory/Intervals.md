## Key Algorithmic Techniques for Intervals 

### Sorting by Start-time and End-time
Sorting is a common pre-processing step that simplifies many interval problems.
- Sort by start-time --> useful for merging intervals or checking overlaps
- Sort by end-time  --> useful for greedy scheduling problems 

### Merging Overlapping Intervals
If two intervals overlap, merge them into one.
- Use a sorted list of intervals
- Iterate through intervals and merge if they overlap

```cpp
vector<vector<int>> merge(vector<vector<int>>& intervals) {
	vector<vector<int>> result;
	sort(intervals.begin(), intervals.end()); // sort by start time 

	for(const auto& interval : intervals) {
		if(result.empty()
		|| result.back()[1] < interval[0]) {
			result.push_back(interval); // no overlap, add new interval
		}
		else {
			result.back()[1] = max(result.back()[1], interval[1]); // merge the overlapping intervals
		}
	}
	return result;
}
```

---
### Use a Min-Heap (Priority Queue) for Scheduling Problems
- a priority queue is useful when we need to track end times of ongoing intervals
- use in problems like Meeting Rooms or CPU Task scheduling

```cpp
int minMeetingRooms(vector<vector<int>>& intervals) {
    sort(intervals.begin(), intervals.end()); // Sort by start time
    priority_queue<int, vector<int>, greater<int>> pq; // Min-heap for end times

    for (auto& interval : intervals) {
        if (!pq.empty() && pq.top() <= interval[0]) {
            pq.pop(); // Remove the finished meeting
        }
        pq.push(interval[1]); // Add the new meeting end time
    }
    return pq.size(); // Number of active meetings
}
```

---
### Greedy Approach for Non-Overlapping Intervals
When asked to remove the fewest number of intervals to make them non-overlapping 
- sort by end time (instead of start time)
- always keep the earliest finishing interval to leave room for others 

```cpp
int eraseOverlapIntervals(vector<vector<int>>& intervals) {
    sort(intervals.begin(), intervals.end(), [](auto& a, auto& b) {
        return a[1] < b[1]; // Sort by end time
    });

    int end = intervals[0][1], count = 0;
    for (int i = 1; i < intervals.size(); i++) {
        if (intervals[i][0] < end) count++; // Overlap found, remove it
        else end = intervals[i][1]; // Update end to the current interval
    }
    return count;
}
```

---
### Sweep Line Algorithm + Event Sorting

Useful for interval problems where we need to track :
- how many intervals are active at a given point
- the maximum number of overlapping intervals

Approach:
- convert intervals into events `(start, +1)` and `(end, -1)`
- sort events: if two events have the same time, process end event first
- keep a running count

```cpp
int maxEvents(vector<vector<int>>& events) {
    vector<pair<int, int>> timeline;
    for (auto& e : events) {
        timeline.emplace_back(e[0], 1);  // Start of event
        timeline.emplace_back(e[1], -1); // End of event
    }
    sort(timeline.begin(), timeline.end()); // Sort by time

    int maxAttend = 0, ongoing = 0;
    for (auto& [time, change] : timeline) {
        ongoing += change;
        maxAttend = max(maxAttend, ongoing);
    }
    return maxAttend;
}
```

---
### Binary Search for Efficient Interval Lookup

If we need to quickly find an interval, we can use binary search (`lower_bound / upper_bound)
Works well when searching for next available intervals

```cpp
vector<int> findRightInterval(vector<vector<int>>& intervals) {
    map<int, int> starts; // Stores {start, index}
    for (int i = 0; i < intervals.size(); i++) starts[intervals[i][0]] = i;

    vector<int> res;
    for (auto& interval : intervals) {
        auto it = starts.lower_bound(interval[1]); // Find the next interval
        res.push_back(it == starts.end() ? -1 : it->second);
    }
    return res;
}
```