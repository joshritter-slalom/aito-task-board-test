# Test-to-production workflow

Use the test repository for structural, visual, and behavioral work. Use production only for approved, validated results.

1. Create a `codex/` feature branch in the test repository.
2. Make the smallest scoped change.
3. Run the build and inspect the rendered board.
4. Open a pull request into test `main`.
5. Validate the merged test result.
6. After explicit approval, create a promotion branch in the production repository.
7. Promote only the approved page asset and any explicitly required navigation metadata. Do not replace the hosting scaffold.
8. Run the production build and open a production pull request.
9. Merge after review. The production `main` pipeline deploys the site.

Routine data refreshes may update the appropriate page automatically after validation. They must not change hosting configuration, authentication, workflows, or another page’s content. A failed refresh must leave production unchanged.
