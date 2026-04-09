# Note: **Controller** autowiring — **`create()`** not always required (Drupal core)

**Project:** [Drupal core](https://www.drupal.org/project/drupal) — **developer reference** (Slack + change record). Use when migrating controllers from **`ControllerBase` + `create()`** to **constructor injection** resolved by the container.

## Summary

Drupal can **autowire** route controllers registered as **services** (or otherwise eligible for container resolution). That means a controller that injects dependencies via **`__construct(...)`** with **type-hinted** services **does not always need** a static **`create(ContainerInterface $container)`** factory method—the pattern that was typical when extending **`ControllerBase`** and pulling services manually.

The canonical write-up is the **change record** [**Controllers can be autowired and a `create()` method is no longer always necessary**](https://www.drupal.org/node/3395716) (published **29 Oct 2023**). It shows **constructor** injection (e.g. **`DateFormatterInterface`**, **`RendererInterface`**, **`EntityRepositoryInterface`**) and explains when **`create()`** is still appropriate.

A related core issue where this came up in discussion: [#3577774](https://www.drupal.org/project/drupal/issues/3577774).

## Pattern (sketch)

- **Prefer** the **change record** and core examples for full **`services.yml`** / route wiring.
- **Idea:** define dependencies in the **constructor**; let the **service container** build the controller when the route references the controller service or the class is autowired per project configuration.

```php
// Illustrative only — align services.yml and route defaults with your module.
public function __construct(
  protected DateFormatterInterface $dateFormatter,
  protected RendererInterface $renderer,
  protected EntityRepositoryInterface $entityRepository,
) {}
```

## References

- Change record: [drupal.org/node/3395716](https://www.drupal.org/node/3395716).
- Core issue (context): [drupal.org/project/drupal/issues/3577774](https://www.drupal.org/project/drupal/issues/3577774).
- Slack (paraphrase): **Sivaji Ganesh** asked for an **autowiring in controller** example while working on **#3577774**; **godotislate** pointed to **node/3395716**; thanks exchanged.
