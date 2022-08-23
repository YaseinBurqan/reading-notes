# Context API - Behaviors

## Snackbars

Snackbars are notifications that show up on the screen when a user performs an action. They are not intrusive at all and appear for just a brief moment. Snackbars fit perfectly on the 'low priority' end of the spectrum for our design system.

## Dream State

From an engineering standpoint, our snackbar system must easy to use and generally be very lightweight. We don't want to deal with a messy React tree and wrappers. Hooks are a perfect fit here - imagine we have a custom hook that lets us do this and work backwards

## Globally Accessible

There's no need for another component somewhere in the tree to hook into that state (at least not in our use-case) The management of that state needs to be globally accessible. Context can let us do just this.

    export const SnackBarContext = createContext()

    export function SnackBarProvider({ children }) {
    const [alerts, setAlerts] = useState([])

    return (
        <SnackBarContext.Provider value={{ setAlerts }}>
        {children}
        {alerts.map((alert) => <SnackBar key={alert}>{alert}</SnackBar>)}
        </SnackBarContext.Provider>
    )
    }

Our custom hook from before is nothing more than a small wrapper around the useContext internal React hook. It turns out that our custom hook is just an internal wrapper for the external useContext hook.

    import { useContext } from 'react'
    import { SnackBarContext } from 'components/snack-bar-provider'
    const useSnackBars = () => useContext(SnackBarContext)
    export default useSnackBars

## Higher Level API & Behaviour

    export const SnackBarContext = createContext()

    const AUTO_DISMISS = 5000

    export function SnackBarProvider({ children }) {
    const [alerts, setAlerts] = useState([])
    
    const activeAlertIds = alerts.join(',')
    useEffect(() => {
        if (activeAlertIds.length > 0) {
        const timer = setTimeout(() => setAlerts((alerts) => alerts.slice(0, alerts.length - 1)), AUTO_DISMISS)
        return () => clearTimeout(timer)
        }
    }, [activeAlertIds])

    const addAlert = (alert) => setAlerts((alerts) => [alert, ...alerts])

    const value = { addAlert }

    return (
        <SnackBarContext.Provider value={value}>
        {children}
        {alerts.map((alert) => <SnackBar key={alert}>{alert}</SnackBar>)}
        </SnackBarContext.Provider>
    )
    }

provider now exposes a new function called addAlert. This function uses the local state mutator useState to properly append a new alert without destroying existing ones. UseEffect makes use of useEffect to display each alert for 5 seconds on the screen, and a timer is kicked off to remove the oldest living alert after a delay.

## Sprinkling in Optimizations

 custom hook is now fully operational. We can add alerts easily from anywhere and our provider will display them for us. Use useMemo to memoize value. There's no need for this object to be re-created every time this provider is rendered - just use the memoization cache.

    const value = useMemo(() => ({ addAlert }), [addAlert])

addAlert faces the same problem as value did. This function is being re-created every single render, which means our new useMemo hook will continue to return a new object every single time. We want to memoize the function just like we did with value.

    const addAlert = useCallback((content) => setAlerts((alerts) => [content, ...alerts]), [])

AddAlert will always maintain referential equality between render and alert. We don't have any dependencies for this memoization. This function doesn't depend on anything but the local state alerts, but we don't need to specify it in the list of dependencies.

## Room for Change

You can replace a lot of what Redux does with useContext and useReducer. The combination of these two hooks means we can have a global state and use reducers, actions, and dispatchers to mutate that global state. To an extent, it's possible.

## [Awesome React Context](https://github.com/diegohaz/awesome-react-context)
