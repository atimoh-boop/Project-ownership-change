# Project Ownership Change Prototype

Interactive CreateAI prototype for transferring project ownership from one user to another.

## Demo

Live demo URL, once GitHub Pages is enabled:

https://atimoh-boop.github.io/Project-ownership-change/

Local prototype file:

`index.html`

## Problem

CreateAI currently supports simple project access roles such as `Can view` and `Can edit`. Project ownership transfers are handled manually by Engineering.

As CreateAI adoption grows, project owners and administrators need a safer self-service way to transfer ownership when project responsibilities change.

## Proposed Solution

Allow a project owner or administrator to transfer ownership to another user directly inside the CreateAI sharing experience.

The prototype keeps the existing CreateAI sharing page pattern and adds an ownership transfer path inside the role dropdown:

- `Can view`
- `Can edit`
- `Change ownership`

Selecting `Change ownership` opens a confirmation modal before the request is sent.

## Prototype Flow

1. Open the CreateAI Share screen.
2. Click a non-owner user's role pill.
3. Choose `Can view` or `Can edit` to update normal access.
4. Choose `Change ownership` to start ownership transfer.
5. Review the confirmation modal.
6. Confirm the request.
7. The selected user becomes `Pending owner`.
8. Use `Simulate acceptance` to complete the transfer.
9. The previous owner becomes `Can edit`.

## Guardrails Represented

- Only the current owner or an administrator should be able to initiate transfer.
- The new owner must already have access to the project.
- The user must confirm before ownership transfer is requested.
- Project access, app configuration, prompts, files, and history remain preserved.
- Transfer activity should be audit logged.
- A pending state can exist before the new owner accepts.

## Product Questions

- Should transfer happen immediately or require acceptance by the new owner?
- Should administrators be able to transfer ownership without current owner approval?
- Should inactive or external users be blocked from becoming owner?
- What notifications should be sent to the old owner, new owner, and admins?
- Is there a rollback window after transfer?
- Should ownership transfer affect marketplace publishing, app deployment, API keys, or billing?

## Engineering Notes

Potential implementation areas:

- Permission check for current actor.
- Recipient eligibility check.
- Ownership transfer endpoint.
- Audit log event.
- Notification or email event.
- Pending transfer state.
- Cancellation and expiration behavior.

## Files

- `index.html`: standalone interactive prototype.
- `index.html.png`: static preview image.
