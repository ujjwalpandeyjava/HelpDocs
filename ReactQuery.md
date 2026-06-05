# React Query (TanStack Query) Notes

## Installation

npm install @tanstack/react-query axios

---

## Setup

* Wrap your app with QueryClientProvider
* Create a QueryClient instance

---

### Advantage over custom hook

| Advantage                    | What it means           | Example                                             |
| ---------------------------- | ----------------------- | --------------------------------------------------- |
| Auto caching                 | Stores API data         | Open same screen → no API call                      |
| Background refetch           | Updates silently        | User sees fresh data                                |
| Auto fetch on mount          | 1st fetch is automatic  | User sees data instant as background fetch is there |
| Loading & error handling     | Built-in states         | `isLoading`, `error`                                |
| Auto abort                   | Built-in                | As same API called/code unmounted - manual too      |
| Sync across components       | Shared data             | Navbar + Page same user data                        |
| Retry mechanism              | Auto retry failed calls | Network fail → retry 3 times                        |
| Pagination & infinite scroll | Easy handling           | Instagram-like feed                                 |
| Devtools                     | Debug easily            | See cache, queries                                  |

---

## Fetch Data (GET APIs) → useQuery

* Used for fetching data
* Runs automatically on component mount

Example: useQuery({ queryKey: ['todos'],queryFn: fetchTodos})

States:

* queryKey → Key for cache
* queryFn → handle data
* data → API response
* isLoading → first load
* isFetching → background fetch
* error → error state

---

## Data Manipulation (Write APIs) → useMutation

* Used for user actions

POST (Create)

* create data

DELETE

* delete data

PUT (Update)

* update data

```Example:
useMutation({
 mutationFn: createTodoApi
})
```

---

## When to use what

useQuery → GET APIs
useMutation → POST, PUT, DELETE, actions (like, register, login)

---

## Refetch / Sync Data

After mutation:

* use invalidateQueries to refresh data

Example:
onSuccess → invalidateQueries(['todos'])

---

## Control API Execution

Disable auto API call:
enabled: false

Manual trigger:
refetch()

---

## Caching

* staleTime → how long data is fresh
* gcTime → how long cache stays in memory

Example:
staleTime: 10000 (10 seconds)

---

## Refetch Behavior

refetchOnMount → refetch on component mount
refetchOnWindowFocus → refetch when tab is active

---

## Abort / Cancel API

* React Query gives a signal
* pass it in fetch/axios

---

## No Cache (force API every time)

staleTime: 0
gcTime: 0
refetchOnMount: 'always'

---

## Polling (auto refresh)

refetchInterval: 5000 (5 seconds)

---

## Best Practices

* useQuery for fetching
* useMutation for actions
* always use queryKey
* separate API layer
* invalidate queries after mutation
* use signal for cancel

---

## Common Mistakes

* using useQuery for POST ❌
* not returning data from API ❌
* wrong staleTime (milliseconds) ❌
* missing queryKey ❌

---

## Simple Flow

1. useQuery → fetch data
2. useMutation → user action
3. invalidateQueries → refresh
4. UI updates automatically

---
