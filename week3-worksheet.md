# Week 3 Lab Worksheet

Name: [Adını yaz]
Program: Software Engineering / Computer Programming
Level I aimed for today: Core

## Before you run the lie
I expect `live done` to print `undefined` because the live JSON data does not contain a `done` property.

## After you run the lie
lecture example, title: undefined
live title: delectus aut autem
live done: undefined

Why did TypeScript allow this?
TypeScript allowed this because `as Task` is a type assertion. It does not check the actual JSON data at runtime. The returned object has no `done` property, so its value is undefined.

## typecheck
src/honest.ts:11:7 - error TS2322: Type 'unknown' is not assignable to type '{ title: string; }'.

11 const task: CreateTask = payload;
         ~~~~

Found 1 error in src/honest.ts:11

## Activity 1
What printed for todo 99999?
HTTP status: 404

What printed for the dead address?
Not tested yet.

Which of those two did fetch throw for?
The 404 response did not throw; it was handled by checking response.ok. The dead-address network failure should enter the catch block, but that experiment has not been run yet.

## Activity 3
Paste the saved / refused lines.
saved: { title: 'Design database schema', status: 'doing', projectId: 1, dueDate: '2026-10-20' }
refused: String must contain at least 1 character(s)
refused: Invalid enum value. Expected 'open' | 'doing' | 'done', received 'finished'
refused: Expected number, received string
refused: Required

Paste the outside-feed output.
imported: { ok: true, task: { title: 'delectus aut autem', status: 'open', projectId: 1 } }
HTTP status: 404
missing todo: null

Why was the raw to-do refused by createTask even though it has a title?
The external to-do has a title, but its fields do not match the create-task schema. It has completed instead of status and does not have projectId.

## Exit question
Where is the boundary in this program, and what do you trust after the data has crossed it?
The boundary is where incoming data is checked with a Zod schema using safeParse. After validation succeeds, I trust the parsed data because it matches the schema.
