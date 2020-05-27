# Chapter 13: Component Cohesion

Which classes belong to what components? This decision is an import one but it has been made in an ad hoc manner based on context alone.

- REP : Reuse/Release Equivalence Principle
- CCP : Common Closure Principle
- CRP: Common Reuse Principle

## REP : The Reuse/Release Equivalence Principle

The last decade has seen the rise of module management tools such as Maven, RVM and Leningen that have grown in prominence due to the large number of reusable components and component libraries that have been created.
People who want to reuse software are unable to do so unless the software is tracked against a release process and given a release number. Software developers need to know what releases are coming and what changes these releases will bring. From a software design and architecture perspective this means that the classes and modules that are formed into a component must belong to a cohesive group. The component must have an overarching theme or purpose that the modules share.

Classes and modules that are grouped together as a part of a component should be released together. They share the same version number and the same release tracking and are included in the same release documentation.

However this advise is weak as it is difficult to explain what is is that binds modules and classes together.However this principle is important because violations are easy to detect and your users will not be as happy with your architectural skills .

## CCP : Common Closure Principle

A component should not have multiple reasons to change. If the code needs to be changed it is better if all of the changes occur in one component rather than being distributed across multiple components . When changes are confined to a single component they only need to redeploy the changed component and do not need to be revalidated or redeployed. With CCP, clases that are likely to change for the same reasons. When two classes are tightly bound together they should change together to minimize workload.

This principle is closely related to the Open Closed Principle (OCP) Classes should be closed for modification but open for extension. Since 100 % closure is not attainable closure must be strategic. Classes are designed so that hey are closed to the most common kinds of changes that we expect or have experienced.CCP gathers together the same types of classes that are closed to the same types of changes so that changes are minimized to a small number of components

CCP is the component form of SRP. SRP tell s to separate methods into different classes if they change for different reasons. The CCP tells us to separate classes int different components if they change for different reasons.

Gather together the things that change together for the same times and for the same reason. Separate those things that change at different times for different reasons.

## CRP: Common Reuse Principle

Don't force users of a component to depend on things that they don't need.

The common reuse principle helps us to decide what classes and modules should be placed int a component. Components that tend to be reused together belong in the same component. Reusable classes collaborate with the other classes that are a port of the reusable abstraction. The CRP states that these are the classes that belong together such as a container class and its associated iterators.

CRP also tells us what classes that we should not keep together in a component. When one component depends on another a dependency is created between the components.The using component depends on the used component. As a result of this dependency, every time that the using component changes, the used component also must change. This is true even if the using component does not care about the changes that are made in the used component.

We want to make sure that the the classes that we put into a component are inseparable.All of the classes that are in the component are inseparable from each other When we depend on a component we must depend on every class in the component

## Relation to ISP

The CRP is the generic version of the ISP. The ISP tells us not to depend on classes that have methods that we don't use

The CRO advises us not to depend on components that have classes that we don’t use.

> Don’t depend on things that you don’t need

The three cohesion principles tend to fight each other .REP and CCP are inclusive principles, while the CRP is an exclusive principle. Good architecture tends to try to resolve the tension between the three. An architect who focuses on REP and CRP will find that that there are too many components that are impacted when there are simple changes being made while one that focuses on REPand CCP will notice that this causes too many unneeded releases to be generated. Find the tension triangle that meet the current concerns of the development team. Usually the only sacrifice is reuse is a good place to start. Project will slide to the left as it matures

## Conclusion

The three principles of component cohesion describes a much more complex variety of cohesion. WHen choosing the classes that must be grouped together into components we must consider the opposite forces included in reusability and in develop-ability. Balancing these forces with the needs of the application is not trivial nor is it dynamic and the partitioning this year may not be appropriate in the next year as the focus changes from developability to reusability
