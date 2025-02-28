*Memoization*
- top-down approach
- stores the results of function calls in a table
- recursive implementation
- entries are filled when needed

*Tabulation:* 
- bottom-up approach
- stores the results of subproblems in a table
- iterative implementation
- entries are filled in a bottom-up manner from the smallest size to the final size

|                      | Tabulation                                                                                                                               | Memoization                                                                                                         |
| -------------------- | ---------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------- |
| *State*              | State transition relation is difficult to think                                                                                          | State transition is easy to think                                                                                   |
| *Code*               | Code gets complication when a lot of conditions are requried                                                                             | Code is easy to write by modifying underlying recursive solution                                                    |
| *Speed*              | Fast, as we do not have recursion call overhead                                                                                          | Slow due to a lot of recursive calls                                                                                |
| *Subproblem solving* | If all subproblems must be solved at least once,<br>a bottom-up algorithm outperforms a top-down memoized algorithm by a constant factor | If some subproblems in the subproblem space don't need to be solved at all, the memoized solution has the advantage |

