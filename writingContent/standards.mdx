---
title: Coding Conventions
---

These are the ground rules for writing code in this project.
The goal is to keep things simple, consistent, predictable, and easy to read.

---

## 1. Null vs Undefined
- Use `null` for empty or missing data, like an account with no email.
- `undefined` should never be used, you should only ever see this if YOU type something wrong, ie access a property that doesn't exist.

This makes testing and debugging easier:
- **`null`** - The data just isn't there (normal)
- **`undefined`** - You messed up somewhere (bug)

```ts
// Good
const user = await db.findUser(id) ?? null;

// Bad
const user = await db.findUser(id); // could return undefined
```

---

## 2. Keep Core Logic in Utils
All core functionality belongs in utility modules, not inside routes or controllers.
This keeps things organized, dry, and easy to test.

For example, `PasswordUtils.ts` should contain:
```ts
export function CreatePasswordHash(password: string): string {
	// Hashing logic
}

export function VerifyPasswordHash(password: string, hash: string): boolean {
	// Verification logic
}
```

Then use these in your routes:
```ts
import { CreatePasswordHash } from './Utils/PasswordUtils';

{
	method: 'POST',
	route: '/register',
	params: {
		username: 'string',
		password: 'string',
	},
	async handler(req, res) {
		const passwordHash = CreatePasswordHash(req.params.password);
		// rest of the code
	}
}
```

Routes should **only call helpers**, never touch the database directly!
```ts
// Good
import { VerifyPasswordHash } from './Utils/PasswordUtils';
import { GetUserByUsername } from './Utils/UserUtils';

{
	method: 'POST',
	route: '/login',
	params: {
		username: 'string',
		password: 'string',
	},
	async handler(req, res) {
		const user = await GetUserByUsername(req.params.username);
		if (!user || !VerifyPasswordHash(req.params.password, user.passwordHash)) {
			return res.status(401).send('Invalid credentials');
		}
		// rest of the code
	}
}

// Bad
{
	method: 'POST',
	route: '/login',
	params: {
		username: 'string',
		password: 'string',
	},
	async handler(req, res) {
		const user = await db.findUser(req.params.username);
		const passwordHash = crypto.createHash('sha256').update(...);
		if (!user || user.passwordHash !== passwordHash) {
			return res.status(401).send('Invalid credentials');
		}
		// rest of the code
	}
}
```

---

## 3. Use `??` When Possible
Use the nullish coalescing operator (`??`) to provide default values for potentially `null` or `undefined` variables.
This is cleaner than using `||`, which can lead to unexpected behavior with falsy values like `0` or `''`.
We understand that sometimes `||` is needed, but try to avoid it when possible. This also ties in nicely with the first point about `null` vs `undefined`.

```ts
// Good
const lastName = user.lastName ?? null;

// Bad
const lastName = user.lastName || null; // lastname could be ''
```

---

## 4. Use `const` and `let` Instead of `var`
Always use `const` for variables that won't change, and `let` for those that will.
Avoid `var` entirely, as it has function scope and can lead to bugs.
```ts
// Good
const MAX_USERS = 100;
let currentUsers = 0;
// Bad
var isLoggedIn = false; // function scope, not block scope
```

---

## 5. Use `async/await` as Much as Possible
You should be using `async/await` as much as reasonably possible.
This keeps your code readable and avoids callback hell.

It also ensures I/O operations (like database queries, API requests, file reads) don't block the event loop while they wait for results.
For CPU intensive tasks (like hashing or image processing), always use the async version of the library if available (`bcrypt.hash()` instead of `bcrypt.hashSync()`).
Synchronous versions will block the event loop and slow everything else down.

```ts
// Good
async function FetchIPs() {
	const blockedIPs = await fs.promises.readFile('blockedIPs.json', 'utf-8');
	return JSON.parse(blockedIPs);
}

// Bad
function FetchIPs() {
	// if the file is large it could stall for a few seconds!
	const blockedIPs = fs.readFileSync('blockedIPs.json', 'utf-8');
	return JSON.parse(blockedIPs);
}
```

---

## 6. Naming Conventions
"There are only 2 hard things in computer science: cache invalidation and naming things." – Phil Karlton

- **Variables**: Use `camelCase` for variables and function names
- **Constants**: Use `SCREAMING_CASE` for constants that never change, ie `MAX_USERS`, `API_KEY`
- **Classes**: Use `PascalCase` for class names, functions, and methods
- **Files**: Use `PascalCase` for file names, e.g. `PasswordUtils.ts`

Names should also be descriptive and meaningful. Avoid abbreviations unless they are well-known (e.g. `URL`, `API`, `DB`). <br/>
`gUByID()` -> `GetUserById()` <br/>
`calcTotPrice()` -> `CalculateTotalPrice()` <br/>
`checkPass()` -> `VerifyPasswordHash()`

---

## 7. Simple Return Types
Functions should only return one type of value, don't make it do everything.
Null values do not count as a different type here.
```ts
function GetUserById(id: string): User | null {
	// Returns a User object or null if not found
}
```

---

## General Philosophy
- Keep it simple and straightforward, don't over-engineer
- Optimize for readability, not performance
- Favor explicitness over magic
- Code should explain itself without a comment
- If you think it might be confusing, it probably is