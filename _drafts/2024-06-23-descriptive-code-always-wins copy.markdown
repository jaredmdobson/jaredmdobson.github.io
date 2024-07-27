---
layout: post
title:  "Descriptive Code Always Wins"
date:   2024-06-23 13:58:23 -0600
---

I use Siri on my phone to set a reminders for appointments, tasks, chores, workouts, grocery items, you name it, i am fully charged on reminders.

When i speak to Siri to set a reminder sometimes she/it mishears what I'm saying and i'll get a reminder like:

```markdown
* Buy new nike mask
```

The funny thing is i can see the reminder on my phone when i'm talking to Siri and I think, I'll remember what i really want, i remember what it is supposed to say.

Well i never do, i'm almost always confused by these misunderstood reminders and i'm just left baffled by them.  Maybe they weren't that important?

This reminder of buying a new nike mask really confused me, i never have owned a nike mask and i wasn't sure what it was, at first i thought it could be:

```markdown
* A gas mask?
* A special covid gas mask?
* A new filter for my gas mask?
```

So i search for a nike mask to see if it sparks any ideas:


<img src="/assets/images/posts/descriptive-code-always-wins/nike-mask.jpg" alt="nike mask" class="small"/>

I cannot possibly think of why i would ever want a mask like this, maybe for the cold or for fitness performance?  Maybe it is a high altitude simulator mask? But I already live in high altitude...

Later the next day i realize what it was supposed to say:
```markdown
* Buy a new sleep mask
```

But even that is not very clear, is this a sleep mask to rejuvenate my face?  Liquid or Light therapy?

<img src="/assets/images/posts/descriptive-code-always-wins/rejuvenating-sleep-mask.jpg" alt="sleep mask" class="small"/>
<img src="/assets/images/posts/descriptive-code-always-wins/light-therapy-mask.jpg" alt="sleep mask" class="small"/>

Or maybe it's not even for me?  

How about if we become way more descriptive the reminder a bit:

```markdown
* Buy myself a new sleep mask that covers my eyes at night so i can sleep better, but not too tight on my face or that covers my nose, like the other one i got on amazon.
```

Now this is good overkill, its good because it is descriptive, everyone knows what i mean. But let's slim it down

```markdown
* Buy myself a new comfortable light blocking eye-covering sleep mask like the last one i bought on amazon.
```

Better still overly wordy and because i have a reference point, my amazon orders to look up the product i can remove more content.

```markdown
* Buy myself another comfortable sleep mask like the last one i bought on amazon.
```

Boom!  We get a (hopefully) static reference point to my amazon orders and plenty of description, reminding me of the last sleep mask i purchased, loved and lost.

Now let's look at some java code:

```java
public class a {
    private UserManager b;
    private PaymentProcessor c;
    private FilterService d;

    public a(UserManager b, PaymentProcessor c, FilterService d) {
        this.b = b;
        this.c = c;
        this.d = d;
    }

    public void e(String f) {
        var g = b.getUserById(f);
        var h = d.getActiveFiltersForUser(f);
        double i = h.stream().mapToDouble(d::getFilterPrice).sum();
        c.chargeUser(g, i);
        System.out.println("Successfully renewed filters and charged user " + g.getName() + " for $" + i);
    }
}
```

```java
import usermanagement.UserManager;
import payment.PaymentProcessor;
import filtermanagement.FilterService;

public class UserSubscriptionService {

    private UserManager userManager;
    private PaymentProcessor paymentProcessor;
    private FilterService filterService;

    public UserSubscriptionService(UserManager userManager, PaymentProcessor paymentProcessor, FilterService filterService) {
        this.userManager = userManager;
        this.paymentProcessor = paymentProcessor;
        this.filterService = filterService;
    }

    /**
     * Fetches the user's active filters, calculates the total charge, and processes the payment.
     * @param userId The ID of the user to process.
     */
    public void renewUserFiltersAndCharge(String userId) {
        // Fetch user details
        var user = userManager.getUserById(userId);
        
        // Fetch user's active filters
        var filters = filterService.getActiveFiltersForUser(userId);
        
        // Calculate total charge for the filters
        double totalCharge = filters.stream().mapToDouble(filterService::getFilterPrice).sum();
        
        // Charge the user
        paymentProcessor.chargeUser(user, totalCharge);
        
        // Log the successful operation
        System.out.println("Successfully renewed filters and charged user " + user.getName() + " for $" + totalCharge);
    }
}
```
