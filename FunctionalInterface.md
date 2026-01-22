# Functional Interface
Interface having exactly single abstract method but can have any number of defaults and static methods.We can invoke lambda expression by using functional interface.
Before 1.8 in functional interface only public abstract method is allowed.

Advantage of @FunctionalInterface:-
   - It restrict the interface to be a Functional Interface.
   - So if people have already used some lambda expression and some new team member added another abstract method in that interface then all lambda expression will have errors.
