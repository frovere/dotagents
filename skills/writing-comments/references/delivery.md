# Delivery by capability

Use the existing connector, API, or repository workflow for the requested destination. Inspect only the capabilities needed for this comment; leave tool syntax, account IDs, and upload limits in their current source of truth. Reuse capability information already established in the session.

## Destination and reply targeting

Confirm the issue, parent discussion, general PR conversation, or review thread before writing. Follow repository tracker instructions for an unspecified destination and the user's explicit destination when supplied. A general conversation comment and a review-thread reply may require different operations.

## Mentions

When a notification is requested, resolve the recipient to the destination account and use its supported mention representation. A typed `@name` alone does not establish notification. If mentions are unavailable, address the person in text and report that notification could not be established.

## Diagram rendering

Choose the path supported by both the harness and destination:

1. **Native rendering:** when the destination supports the diagram format, insert the source using the supported representation and check its rendering.
2. **Image rendering:** otherwise use an existing renderer, repository command, or browser harness to produce a legible PNG. Use SVG only when the destination supports displaying it. Keep the source beside the image for revisions.
3. **Connected drawing integration:** when available and authorized, create editable shapes and export or capture just the diagram. For example, a tldraw integration may support Mermaid conversion and image export or screenshots; load its skill and inspect the available operations. Use a designated or already-authorized board; create a new board only when requested. If no board is authorized, continue through another available path.
4. **Alternate renderer:** a small flow can be translated to another installed renderer, preserving all conditions and branches.
5. **Text:** when no image-producing path is usable, provide a short numbered flow or compact text diagram. State the capability gap if the requested deliverable requires an image.

Prefer a supported export or screenshot result that the harness can transfer to a file. Copy rendered pixels rather than canvas shapes when using a clipboard. An image visible only to the agent is not yet a transferable attachment. Check the actual export result before promising a file.

Inspect the diagram for readable labels, complete branches, and clipping. Pair the visual with the short explanation and next action the recipient needs.

## Attachments and inline media

Use the destination's supported upload mechanism. Preserve original evidence rather than treating a temporary signed playback URL as a durable attachment.

If inline images are supported, insert the uploaded image with the returned reference. If only attachments are supported, attach it to the issue or PR and link the attachment from the comment. Report attachment-only delivery accurately. An editable drawing link can supplement the image.

Check the actual comment for a promised embed. Successful upload, a working media URL, and media rendered inside the comment are different observations. When authenticated visual verification is unavailable, report exactly which property remains unverified.

## Publication, readback, and retries

Publish or edit only within the user's existing authorization. A comment request does not itself request a status, assignee, description, review-submission, or thread-resolution change.

Use a returned permalink or identifier to read back the result. When the outcome is uncertain, inspect the destination before retrying to avoid duplicate comments. If readback is unavailable, distinguish the write result from independently verified delivery.
