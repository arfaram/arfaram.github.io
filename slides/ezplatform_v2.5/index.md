# eZ Roadshow 2019

<img class="center scale80" src="img/ezroadshow2019.png" title="eZ Platform ezroadshow 2019" />

---

# eZ Platform v2.4 Features- Recap

--

# Content workflows as state machines

--

## Key Benefits:

- User Interface Integration
- Role and policies-based access control
- User or Groups Notification
- Multisite ability
- Extendable using event listeners delivered with Symfony Workflow Component

--

## Simple Editorial workflow

<img class="center scale50" src="img/2.4/workflows/workflow_diagram.png" alt="eZ Platform 2.x workflows" />

--

## Advanced Editorial workflow

<img class="center" src="img/2.4/workflows/workflow_graph_advanced.png" alt="eZ Platform 2.x workflows" />

--

## Configuration

<img class="center scale80" src="img/2.4/workflows/ez_workflow_configuration.png" alt="eZ Platform 2.x workflows" />

--

## UI integration

<img class="center scale80" src="img/2.4/workflows/ez_workflow_ui.png" alt="eZ Platform 2.x workflows" />

--

## Editors content tree access

<img class="center scale80" src="img/2.4/workflows/backend_access.png" alt="eZ Platform 2.x workflows" />

--

## User groups

<img class="center scale60" src="img/2.4/workflows/user_groups.png" title="" />

--

## Role and Policies

--

## <span class="orange_text">Blogger</span>

<img class="center scale80" src="img/2.4/workflows/role_blogger.png" title="eZ Platform Role and Policies" />

--

## <span class="orange_text">Designer</span>

<img class="center scale90" src="img/2.4/workflows/role_designer.png" title="eZ Platform Role and Policies" />

--

## <span class="orange_text">Reviewer</span>

<img class="center" src="img/2.4/workflows/role_reviewer.png" title="eZ Platform Role and Policies" />

--

## <span class="orange_text">Publisher</span>

<img class="center" src="img/2.4/workflows/role_publisher.png" title="eZ Platform Role and Policies" />

--

## Content edit

--

<img class="center" src="img/2.4/workflows/edit_content_blogger.png" title="eZ Platform Workflow Content edit" />

--

<img class="center" src="img/2.4/workflows/edit_content_designer.png" title="eZ Platform Workflow Content edit" />

--

<img class="center" src="img/2.4/workflows/edit_content_reviewer.png" title="eZ Platform Workflow Content edit" />

--

<img class="center" class="scale90" src="img/2.4/workflows/edit_content_publisher.png" title="eZ Platform Workflow Content edit" />

--

## Notifications

<img class="center scale90" src="img/2.4/workflows/dashboard_queue.png" title="eZ Platform Workflow Content edit" />


--

## Using Events

When a state transition is initiated, the events are dispatched in the following order:

- workflow.guard
- workflow.leave
- workflow.transition
- workflow.enter
- workflow.entered
- workflow.completed
- workflow.announce


&#9758; [Symfony Events doc](https://symfony.com/doc/current/workflow.html#using-events)

--

Each step has three events that are fired in order:

- An event for every workflow (global)
- An event for the workflow concerned
- An event for the workflow concerned with the specific transition or place name

--

## Listen to Events

- Block content publishing
	- using `workflow.guard`: Validate whether the transition is allowed at all

```
public static function getSubscribedEvents()
{
    return [
        'workflow.<workfolw_name>.guard' => ['guardReview'],
    ];
}
public function guardReview(GuardEvent $event)
{
        $subject = $event->getSubject();
        if( $subject instanceof Content && count($subject->getFieldValue('relations')->destinationContentIds) < 2 ) {
                $event->setBlocked('true');
                $this->notificationHandler->error(
                        'You should add at least two relations to this content'
                );
        }
}
```

Note: image size too large, image meta data(copyright, camera:sony/ should be canon ;). Relation to other product with empty stock(warning), number of relations is not satisfied, ...  

--

- Automatically publishing when the last stage/place is reached: done
	- using `workflow.entered`: The subject has entered in the places and the marking is updated (making it a good place to flush data in Doctrine).

```
public static function getSubscribedEvents()
{
    return [
        'workflow.<workfolw_name>.entered.done' => ['publishOnDone'],
    ];
}
public function publishOnDone(Event $event)
{
    $subject = $event->getSubject();
    $this->repository->sudo(function () use ($subject) {
            $this->contentService->publishVersion( $subject->versionInfo );
            $this->notificationHandler->success(
                'Content successfully published'
            );
        });
}
```

--


## Full Release updates

&#9758; [eZ Platform v2.4 Release](https://doc.ezplatform.com/en/latest/releases/ez_platform_v2.4/)

&#9758; [2.4 Features](https://arfaram.github.io/slides/ezplatform_v2.4)
