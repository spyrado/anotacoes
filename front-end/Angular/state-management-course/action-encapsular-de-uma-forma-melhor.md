# Como facilitar a leitura de uma action?

### Como transformar a leitura

#### dessa forma:
```typescript
this.store.dispatch(login({ user }))
```
#### para essa:
```typescript
this.store.dispatch(AuthActions.login({ user }))
```

#### dado o seguinte exemplo:

##### estrutura de pastas:
- 📂 auth/
  - 📂 actions/
    - 📄 auth.actions.ts
    - 📄 action-types.ts

**arquivo**: *auth.actions.ts*
```typescript
import { createAction, props } from "@ngrx/store";
import { User } from "./model/user.model";

export const login = createAction(
  "[Login Page] User Login",
  props<{ user: User }>()
);

export const logout = createAction(
  "[Top Menu] Logout"
);
```

**arquivo**: *action-types.ts*
```typescript
import * as AuthActions from './auth.actions';

export {AuthActions};
```

#### exemplo de uso em algum componente.

**arquivo**: *login.component.ts*
```typescript

  import { AuthActions } from '../action-types';

  login() {
    this.store.dispatch(AuthActions.login({ user }))
  }
```

> com essa implementação simples já é possível importar em qualquer lugar do código e utilizar de maneira mais legível.