# React-projects
just react projects for learning

# React
- React is used for UI creation
- React create a virtual DOM like browser DOM
- React compare browser DOM tree to virtual DOM
- After comparing with Browser DOM react make changes only to the updated part

# React Hooks 

import { hookExample } from 'react'

- useState(): useState hook is use to set variable and give power to update in UI
```React
const [name, setName] = useState("Aman")
```
- useEffect(): this hook use to run a part of code when something is changed
```React
useEffect( () => {}, [] )
```
- useRef(): this hook used when you don't need to render that part of code
```React
let refOne = useRef(0 | null) {// you can use either '0' or 'null', based on your requirement}
```
# Prop Drilling
### Suppose
- we have a react page with nested components
  ```javascript
  
  <App />
  ------------------------------------
  |  <Deshboard />                   |
  |  ------------------------------  |
  |  |  <User />        --------- |  |
  |  |                  | name  | |  |
  |  |                  --------- |  |
  |  ------------------------------  |
  ------------------------------------
  
  ```
- we have 2 component Deshboard and User in the App 
- User have 1 prop name User, in User we have to pass the data name and we don't have the direct acces of the name,
- we getting the name thorugh "Prop Drilling"

### like this
  ```javascript
  
  <App name=""/>
  ------------------------------------
  |  <Deshboard name=""/>            |
  |  ------------------------------  |
  |  |  <User name=""/> --------- |  |
  |  |                  | name  | |  |
  |  |                  --------- |  |
  |  ------------------------------  |
  ------------------------------------
  
  ```


# Context API
- Context API is a way to manage states in react,
- and context API is also help to prevent prop drilling

## To create Context API 
- create files and folder with .js, then

``` javascript
// in one file all setup of Context API

//importing nessesry 
import { useContext, createContext } from 'react'

//creating Context
export const UserContext = cereatContext({
  user: {
    id: 1,
    name: "user",
    email: "mail@mail.com"
  }
  login: (id, password)=>{}
})

//creating hook for context 
export const useUser = () => {
  reture useContext(UserContext)
}

//creating Provider
export const UserProvider = UserContext.Provider

```
## To use Context API 
- go to App component 

``` javascript

//importing nessesry
import { UserProvider } from 'path'

export default function App(){
  //useState and other Hooks

  return(
    <UserProvider value={{user, login}}>

      //Code

    </UserProvider>
  )
}

```