<h1 data-toc-skip="" style="box-sizing: border-box; margin-top: 3rem; margin-bottom: 1.5rem; font-weight: 400; line-height: 1.2; font-size: 1.9rem; color: var(--heading-color); font-family: Lato, &quot;Microsoft Yahei&quot;, sans-serif; font-style: normal; font-variant-ligatures: normal; font-variant-caps: normal; letter-spacing: normal; orphans: 2; text-align: left; text-indent: 0px; text-transform: none; widows: 2; word-spacing: 0px; -webkit-text-stroke-width: 0px; white-space: normal; background-color: rgb(255, 255, 255); text-decoration-thickness: initial; text-decoration-style: initial; text-decoration-color: initial;">Spring find annotated classes</h1><div class="post-meta text-muted" style="box-sizing: border-box; color: rgb(108, 117, 125) !important; font-size: 0.85rem; word-spacing: 1px; font-family: &quot;Source Sans Pro&quot;, &quot;Microsoft Yahei&quot;, sans-serif; font-style: normal; font-variant-ligatures: normal; font-variant-caps: normal; font-weight: 400; letter-spacing: normal; orphans: 2; text-align: left; text-indent: 0px; text-transform: none; widows: 2; -webkit-text-stroke-width: 0px; white-space: normal; background-color: rgb(255, 255, 255); text-decoration-thickness: initial; text-decoration-style: initial; text-decoration-color: initial;"><span style="box-sizing: border-box;">Posted<span> </span><em class="" data-toggle="tooltip" data-placement="bottom" data-original-title="Mon, Aug 24, 2015 12:01 AM" title="" style="box-sizing: border-box; font-style: normal; color: var(--text-color);">Aug 24, 2015</em><span> </span></span><span style="box-sizing: border-box;"><span> </span>Updated<span> </span><em class="" data-toggle="tooltip" data-placement="bottom" data-original-title="Thu, Jun 8, 2023 11:35 AM" title="" style="box-sizing: border-box; font-style: normal; color: var(--text-color);">Jun 8, 2023</em></span><div class="d-flex justify-content-between" style="box-sizing: border-box; display: flex !important; justify-content: space-between !important;"><span style="box-sizing: border-box;">By<span> </span><em style="box-sizing: border-box; font-style: normal; color: var(--text-color);"><a href="https://twitter.com/rudaliszka" style="box-sizing: border-box; color: var(--text-color); text-decoration: none; background-color: transparent;">Przemysław Wojnowski</a></em></span><div style="box-sizing: border-box;"><span class="readtime" data-toggle="tooltip" data-placement="bottom" title="" data-original-title="514 words" style="box-sizing: border-box;"><em style="box-sizing: border-box; font-style: normal; color: var(--text-color);">2 min</em><span> </span>read</span></div></div></div><div class="post-content" style="box-sizing: border-box; font-size: 1.03rem; margin-top: 2rem; overflow-wrap: break-word; color: rgb(52, 52, 60); font-family: &quot;Source Sans Pro&quot;, &quot;Microsoft Yahei&quot;, sans-serif; font-style: normal; font-variant-ligatures: normal; font-variant-caps: normal; font-weight: 400; letter-spacing: normal; orphans: 2; text-align: left; text-indent: 0px; text-transform: none; widows: 2; word-spacing: 0px; -webkit-text-stroke-width: 0px; white-space: normal; background-color: rgb(255, 255, 255); text-decoration-thickness: initial; text-decoration-style: initial; text-decoration-color: initial;"><p style="box-sizing: border-box; margin-top: 0px; margin-bottom: 1rem;">How to find annotated classes using<span> </span><strong style="box-sizing: border-box; font-weight: bolder;">Spring Framework</strong><span> </span>and read metadata from them? Sometimes you may want to attach metadata to your classes using custom annotations. Here’s an example how you can leverage<span> </span><strong style="box-sizing: border-box; font-weight: bolder;">Spring</strong>’s classpath scanning mechanism to do that.</p><h2 id="the-spring-bean-problem" style="box-sizing: border-box; margin-top: 2.5rem; margin-bottom: 1.25rem; font-weight: 400; line-height: 1.2; font-size: 1.5rem; color: var(--heading-color); font-family: Lato, &quot;Microsoft Yahei&quot;, sans-serif;"><span class="mr-2" style="box-sizing: border-box; margin-right: 0.5rem !important;">The Spring Bean problem</span><a href="https://farenda.com/spring-find-annotated-classes/#the-spring-bean-problem" class="anchor text-muted" style="box-sizing: border-box; color: rgb(108, 117, 125) !important; text-decoration: none; background-color: transparent; font-size: 19.2px; visibility: hidden; opacity: 0; transition: opacity 0.25s ease-in 0s, visibility 0s ease-in 0.25s; border-bottom: 1px solid var(--link-underline-color);"><i class="fas fa-hashtag" style="box-sizing: border-box; -webkit-font-smoothing: antialiased; display: inline-block; font-style: normal; font-variant: normal; text-rendering: auto; line-height: 1; font-family: &quot;Font Awesome 5 Free&quot;; font-weight: 900; user-select: none;"></i></a></h2><p style="box-sizing: border-box; margin-top: 0px; margin-bottom: 1rem;">If you use Spring annotations like<span> </span><strong style="box-sizing: border-box; font-weight: bolder;">@Component</strong>,<span> </span><strong style="box-sizing: border-box; font-weight: bolder;">@Repository</strong><span> </span>or<span> </span><strong style="box-sizing: border-box; font-weight: bolder;">@Service</strong>, then Spring will find such classes, but will make them Spring beans.</p><h2 id="classpath-scanner-customization" style="box-sizing: border-box; margin-top: 2.5rem; margin-bottom: 1.25rem; font-weight: 400; line-height: 1.2; font-size: 1.5rem; color: var(--heading-color); font-family: Lato, &quot;Microsoft Yahei&quot;, sans-serif;"><span class="mr-2" style="box-sizing: border-box; margin-right: 0.5rem !important;">Classpath Scanner customization</span><a href="https://farenda.com/spring-find-annotated-classes/#classpath-scanner-customization" class="anchor text-muted" style="box-sizing: border-box; color: rgb(108, 117, 125) !important; text-decoration: none; background-color: transparent; font-size: 19.2px; visibility: hidden; opacity: 0; transition: opacity 0.25s ease-in 0s, visibility 0s ease-in 0.25s; border-bottom: 1px solid var(--link-underline-color);"><i class="fas fa-hashtag" style="box-sizing: border-box; -webkit-font-smoothing: antialiased; display: inline-block; font-style: normal; font-variant: normal; text-rendering: auto; line-height: 1; font-family: &quot;Font Awesome 5 Free&quot;; font-weight: 900; user-select: none;"></i></a></h2><p style="box-sizing: border-box; margin-top: 0px; margin-bottom: 1rem;">Good news is that Spring classpath scanning mechanism is configurable and available in any Spring application. To use custom annotations we have to create an instance of ClassPathScanningCandidateComponentProvider and set appropriate filter - here it is<span> </span><strong style="box-sizing: border-box; font-weight: bolder;">AnnotationTypeFilter</strong>. It returns<span> </span><strong style="box-sizing: border-box; font-weight: bolder;">BeanDefinitions</strong><span> </span>that contains names of found class from which we can get detailed information. The following example will clarify that.</p><h2 id="own-annotations" style="box-sizing: border-box; margin-top: 2.5rem; margin-bottom: 1.25rem; font-weight: 400; line-height: 1.2; font-size: 1.5rem; color: var(--heading-color); font-family: Lato, &quot;Microsoft Yahei&quot;, sans-serif;"><span class="mr-2" style="box-sizing: border-box; margin-right: 0.5rem !important;">Own annotations</span><a href="https://farenda.com/spring-find-annotated-classes/#own-annotations" class="anchor text-muted" style="box-sizing: border-box; color: rgb(108, 117, 125) !important; text-decoration: none; background-color: transparent; font-size: 19.2px; visibility: hidden; opacity: 0; transition: opacity 0.25s ease-in 0s, visibility 0s ease-in 0.25s; border-bottom: 1px solid var(--link-underline-color);"><i class="fas fa-hashtag" style="box-sizing: border-box; -webkit-font-smoothing: antialiased; display: inline-block; font-style: normal; font-variant: normal; text-rendering: auto; line-height: 1; font-family: &quot;Font Awesome 5 Free&quot;; font-weight: 900; user-select: none;"></i></a></h2><p style="box-sizing: border-box; margin-top: 0px; margin-bottom: 1rem;">We create our custom annotation that allows us to attach some metatdata:</p><div class="language-java highlighter-rouge" style="box-sizing: border-box; border-radius: 6px; background: var(--highlight-bg-color); color: var(--highlighter-rouge-color); margin-top: 0.5rem; margin-bottom: 1.2em;"><div class="code-header" style="box-sizing: border-box; user-select: none; display: flex; justify-content: space-between; align-items: center; height: 2.25rem;"><span data-label-text="Java" style="box-sizing: border-box;"><i class="fas fa-code small" style="box-sizing: border-box; font-size: 11.536px; font-weight: 900; -webkit-font-smoothing: antialiased; display: inline-block; font-style: normal; font-variant: normal; text-rendering: auto; line-height: 1; font-family: &quot;Font Awesome 5 Free&quot;; user-select: none; margin-right: 0.4rem; color: var(--code-header-icon-color);"></i></span><button aria-label="copy" data-title-succeed="Copied!" data-original-title="" title="" style="box-sizing: border-box; border-radius: 6px; margin: 0px; font-family: inherit; font-size: inherit; line-height: inherit; overflow: visible; text-transform: none; appearance: button; cursor: pointer; border: 1px solid rgba(0, 0, 0, 0); height: 2.25rem; width: 2.25rem; padding: 0px; background-color: inherit;"><i class="far fa-clipboard" style="box-sizing: border-box; -webkit-font-smoothing: antialiased; display: inline-block; font-style: normal; font-variant: normal; text-rendering: auto; line-height: 1; font-weight: 400; font-family: &quot;Font Awesome 5 Free&quot;; user-select: none; color: var(--code-header-icon-color);"></i></button></div><div class="highlight" style="box-sizing: border-box; border-radius: 6px; background: var(--highlight-bg-color); overflow: auto; padding-top: 0.5rem; padding-bottom: 1rem;"><code style="box-sizing: border-box; font-family: SFMono-Regular, Menlo, Monaco, Consolas, &quot;Liberation Mono&quot;, &quot;Courier New&quot;, monospace; font-size: 14.42px; color: rgba(0, 0, 0, 0); overflow-wrap: break-word; hyphens: none;">

1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 | package com.farenda.java.lang;  import java.lang.annotation.ElementType; import java.lang.annotation.Retention; import java.lang.annotation.RetentionPolicy; import java.lang.annotation.Target;  // Make the annotation available at runtime: @Retention(RetentionPolicy.RUNTIME) // Allow to use only on types: @Target(ElementType.TYPE) public @interface Findable {      /**      * User friendly name of annotated class.      */     String name(); }
-- | --


</code></div></div><h2 id="summary" style="box-sizing: border-box; margin-top: 2.5rem; margin-bottom: 1.25rem; font-weight: 400; line-height: 1.2; font-size: 1.5rem; color: var(--heading-color); font-family: Lato, &quot;Microsoft Yahei&quot;, sans-serif;"><span class="mr-2" style="box-sizing: border-box; margin-right: 0.5rem !important;">Summary</span><a href="https://farenda.com/spring-find-annotated-classes/#summary" class="anchor text-muted" style="box-sizing: border-box; color: rgb(108, 117, 125) !important; text-decoration: none; background-color: transparent; font-size: 19.2px; visibility: hidden; opacity: 0; transition: opacity 0.25s ease-in 0s, visibility 0s ease-in 0.25s; border-bottom: 1px solid var(--link-underline-color);"><i class="fas fa-hashtag" style="box-sizing: border-box; -webkit-font-smoothing: antialiased; display: inline-block; font-style: normal; font-variant: normal; text-rendering: auto; line-height: 1; font-family: &quot;Font Awesome 5 Free&quot;; font-weight: 900; user-select: none;"></i></a></h2><p style="box-sizing: border-box; margin-top: 0px; margin-bottom: 1rem;">This sort of scanning is very good fit for applications that already use Spring Framework. However, in the future, we’ll see how to solve the same problem, but without Spring.</p></div>Spring find annotated classes
Posted Aug 24, 2015  Updated Jun 8, 2023
By [Przemysław Wojnowski](https://twitter.com/rudaliszka)
2 min read
How to find annotated classes using Spring Framework and read metadata from them? Sometimes you may want to attach metadata to your classes using custom annotations. Here’s an example how you can leverage Spring’s classpath scanning mechanism to do that.

The Spring Bean problem
If you use Spring annotations like @Component, @Repository or @Service, then Spring will find such classes, but will make them Spring beans.

Classpath Scanner customization
Good news is that Spring classpath scanning mechanism is configurable and available in any Spring application. To use custom annotations we have to create an instance of ClassPathScanningCandidateComponentProvider and set appropriate filter - here it is AnnotationTypeFilter. It returns BeanDefinitions that contains names of found class from which we can get detailed information. The following example will clarify that.

Own annotations
We create our custom annotation that allows us to attach some metatdata:

package com.farenda.java.lang;

import java.lang.annotation.ElementType;
import java.lang.annotation.Retention;
import java.lang.annotation.RetentionPolicy;
import java.lang.annotation.Target;

// Make the annotation available at runtime:
@Retention(RetentionPolicy.RUNTIME)
// Allow to use only on types:
@Target(ElementType.TYPE)
public @interface Findable {

    /**
     * User friendly name of annotated class.
     */
    String name();
}
Adding metadata to own classes
Sample classes annotated with the custom annotation:

package com.farenda.java.lang;

@Findable(name = "Find me")
public class FirstAnnotatedClass {
}

package com.farenda.java.lang;

@Findable(name = "Find me too")
public class SecondAnnotatedClass {
}
Spring dependency
The classpath scanner is provided by spring-context project. Here’s the relevant Maven dependency:

<dependency>
    <groupId>org.springframework</groupId>
    <artifactId>spring-context</artifactId>
    <version>4.2.0.RELEASE</version>
</dependency>
The Scanner
The Java code below is using ClassPathScanningCandidateComponentProvider to scan classes in com.farenda.java.lang package.

package com.farenda.java.lang;

import org.springframework.beans.factory.config.BeanDefinition;
import org.springframework.context.annotation.ClassPathScanningCandidateComponentProvider;
import org.springframework.core.type.filter.AnnotationTypeFilter;

public class SpringClassScanner {

    public static void main(String[] args) throws Exception {
        System.out.println("Finding annotated classes using Spring:");
        new SpringClassScanner().findAnnotatedClasses("com.farenda.java.lang");
    }

    public void findAnnotatedClasses(String scanPackage) {
        ClassPathScanningCandidateComponentProvider provider = createComponentScanner();
        for (BeanDefinition beanDef : provider.findCandidateComponents(scanPackage)) {
            printMetadata(beanDef);
        }
    }

    private ClassPathScanningCandidateComponentProvider createComponentScanner() {
        // Don't pull default filters (@Component, etc.):
        ClassPathScanningCandidateComponentProvider provider
                = new ClassPathScanningCandidateComponentProvider(false);
        provider.addIncludeFilter(new AnnotationTypeFilter(Findable.class));
        return provider;
    }

    private void printMetadata(BeanDefinition beanDef) {
        try {
            Class<?> cl = Class.forName(beanDef.getBeanClassName());
            Findable findable = cl.getAnnotation(Findable.class);
            System.out.printf("Found class: %s, with meta name: %s%n",
                    cl.getSimpleName(), findable.name());
        } catch (Exception e) {
            System.err.println("Got exception: " + e.getMessage());
        }
    }
}
The code is straightforward. The hardest thing is to type and read very long names of Spring classes. ;-)

And here’s the output of running the code:

Finding annotated classes using Spring:
Found class: SecondAnnotatedClass, with meta name: Find me too
Found class: FirstAnnotatedClass, with meta name: Find me
Summary
This sort of scanning is very good fit for applications that already use Spring Framework. However, in the future, we’ll see how to solve the same problem, but without Spring.

---

<h1 data-toc-skip="" style="box-sizing: border-box; margin-top: 3rem; margin-bottom: 1.5rem; font-weight: 400; line-height: 1.2; font-size: 1.9rem; color: var(--heading-color); font-family: Lato, &quot;Microsoft Yahei&quot;, sans-serif;">Spring component scan exclude</h1><div class="post-meta text-muted" style="box-sizing: border-box; color: rgb(108, 117, 125) !important; font-size: 0.85rem; word-spacing: 1px;"><span style="box-sizing: border-box;">Posted<span> </span><em class="" data-toggle="tooltip" data-placement="bottom" data-original-title="Sun, Dec 20, 2015 11:01 PM" title="" style="box-sizing: border-box; font-style: normal; color: var(--text-color);">Dec 20, 2015</em><span> </span></span><span style="box-sizing: border-box;"><span> </span>Updated<span> </span><em class="" data-toggle="tooltip" data-placement="bottom" data-original-title="Thu, Jun 8, 2023 11:35 AM" title="" style="box-sizing: border-box; font-style: normal; color: var(--text-color);">Jun 8, 2023</em></span><div class="d-flex justify-content-between" style="box-sizing: border-box; display: flex !important; justify-content: space-between !important;"><span style="box-sizing: border-box;">By<span> </span><em style="box-sizing: border-box; font-style: normal; color: var(--text-color);"><a href="https://twitter.com/rudaliszka" style="box-sizing: border-box; color: var(--text-color); text-decoration: none; background-color: transparent;">Przemysław Wojnowski</a></em></span><div style="box-sizing: border-box;"><span class="readtime" data-toggle="tooltip" data-placement="bottom" title="" data-original-title="473 words" style="box-sizing: border-box;"><em style="box-sizing: border-box; font-style: normal; color: var(--text-color);">2 min</em><span> </span>read</span></div></div></div><div class="post-content" style="box-sizing: border-box; font-size: 1.03rem; margin-top: 2rem; overflow-wrap: break-word;"><p style="box-sizing: border-box; margin-top: 0px; margin-bottom: 1rem; color: rgb(52, 52, 60); font-family: &quot;Source Sans Pro&quot;, &quot;Microsoft Yahei&quot;, sans-serif; font-size: 16.48px; font-style: normal; font-variant-ligatures: normal; font-variant-caps: normal; font-weight: 400; letter-spacing: normal; orphans: 2; text-align: left; text-indent: 0px; text-transform: none; widows: 2; word-spacing: 0px; -webkit-text-stroke-width: 0px; white-space: normal; background-color: rgb(255, 255, 255); text-decoration-thickness: initial; text-decoration-style: initial; text-decoration-color: initial;">How to<span> </span><strong style="box-sizing: border-box; font-weight: bolder;">exclude classes/packages</strong><span> </span>from<span> </span><strong style="box-sizing: border-box; font-weight: bolder;">Component Scan</strong><span> </span>in<span> </span><strong style="box-sizing: border-box; font-weight: bolder;">Spring Framework</strong>? The task is a bit tricky, especially when<span> </span><strong style="box-sizing: border-box; font-weight: bolder;">regexp</strong><span> </span>is involved. See how it works!</p><h1 id="example-spring-beans" style="box-sizing: border-box; margin-top: 3rem; margin-bottom: 1.5rem; font-weight: 400; line-height: 1.2; font-size: 1.9rem; color: var(--heading-color); font-family: Lato, &quot;Microsoft Yahei&quot;, sans-serif; font-style: normal; font-variant-ligatures: normal; font-variant-caps: normal; letter-spacing: normal; orphans: 2; text-align: left; text-indent: 0px; text-transform: none; widows: 2; word-spacing: 0px; -webkit-text-stroke-width: 0px; white-space: normal; background-color: rgb(255, 255, 255); text-decoration-thickness: initial; text-decoration-style: initial; text-decoration-color: initial;">Example Spring beans</h1><p style="box-sizing: border-box; margin-top: 0px; margin-bottom: 1rem; color: rgb(52, 52, 60); font-family: &quot;Source Sans Pro&quot;, &quot;Microsoft Yahei&quot;, sans-serif; font-size: 16.48px; font-style: normal; font-variant-ligatures: normal; font-variant-caps: normal; font-weight: 400; letter-spacing: normal; orphans: 2; text-align: left; text-indent: 0px; text-transform: none; widows: 2; word-spacing: 0px; -webkit-text-stroke-width: 0px; white-space: normal; background-color: rgb(255, 255, 255); text-decoration-thickness: initial; text-decoration-style: initial; text-decoration-color: initial;">Let’s say that we’ve got the following two classes in<span> </span><strong style="box-sizing: border-box; font-weight: bolder;">com.farenda.java.spring.excludescan</strong><span> </span>package:</p><div class="language-java highlighter-rouge" style="box-sizing: border-box; border-radius: 6px; background: var(--highlight-bg-color); color: var(--highlighter-rouge-color); margin-top: 0.5rem; margin-bottom: 1.2em; font-family: &quot;Source Sans Pro&quot;, &quot;Microsoft Yahei&quot;, sans-serif; font-size: 16.48px; font-style: normal; font-variant-ligatures: normal; font-variant-caps: normal; font-weight: 400; letter-spacing: normal; orphans: 2; text-align: left; text-indent: 0px; text-transform: none; widows: 2; word-spacing: 0px; -webkit-text-stroke-width: 0px; white-space: normal; text-decoration-thickness: initial; text-decoration-style: initial; text-decoration-color: initial;"><div class="code-header" style="box-sizing: border-box; user-select: none; display: flex; justify-content: space-between; align-items: center; height: 2.25rem;"><span data-label-text="Java" style="box-sizing: border-box;"><i class="fas fa-code small" style="box-sizing: border-box; font-size: 11.536px; font-weight: 900; -webkit-font-smoothing: antialiased; display: inline-block; font-style: normal; font-variant: normal; text-rendering: auto; line-height: 1; font-family: &quot;Font Awesome 5 Free&quot;; user-select: none; margin-right: 0.4rem; color: var(--code-header-icon-color);"></i></span><button aria-label="copy" data-title-succeed="Copied!" data-original-title="" title="" style="box-sizing: border-box; border-radius: 6px; margin: 0px; font-family: inherit; font-size: inherit; line-height: inherit; overflow: visible; text-transform: none; appearance: button; cursor: pointer; border: 1px solid rgba(0, 0, 0, 0); height: 2.25rem; width: 2.25rem; padding: 0px; background-color: inherit;"><i class="far fa-clipboard" style="box-sizing: border-box; -webkit-font-smoothing: antialiased; display: inline-block; font-style: normal; font-variant: normal; text-rendering: auto; line-height: 1; font-weight: 400; font-family: &quot;Font Awesome 5 Free&quot;; user-select: none; color: var(--code-header-icon-color);"></i></button></div><div class="highlight" style="box-sizing: border-box; border-radius: 6px; background: var(--highlight-bg-color); overflow: auto; padding-top: 0.5rem; padding-bottom: 1rem;"><code style="box-sizing: border-box; font-family: SFMono-Regular, Menlo, Monaco, Consolas, &quot;Liberation Mono&quot;, &quot;Courier New&quot;, monospace; font-size: 14.42px; color: rgba(0, 0, 0, 0); overflow-wrap: break-word; hyphens: none;">

1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20 21 22 23 | package com.farenda.java.spring.excludescan;  import org.springframework.stereotype.Service;  @Service public class ExcludedService {      public ExcludedService() {         System.out.println("Instantiating " + getClass().getSimpleName());     } }  package com.farenda.java.spring.excludescan;  import org.springframework.stereotype.Service;  @Service public class IncludedService {      public IncludedService() {         System.out.println("Instantiating " + getClass().getSimpleName());     } }
-- | --


</code></div></div><br class="Apple-interchange-newline">Spring component scan exclude
Posted Dec 20, 2015  Updated Jun 8, 2023
By [Przemysław Wojnowski](https://twitter.com/rudaliszka)
2 min read
How to exclude classes/packages from Component Scan in Spring Framework? The task is a bit tricky, especially when regexp is involved. See how it works!

Example Spring beans
Let’s say that we’ve got the following two classes in com.farenda.java.spring.excludescan package:

package com.farenda.java.spring.excludescan;

import org.springframework.stereotype.Service;

@Service
public class ExcludedService {

    public ExcludedService() {
        System.out.println("Instantiating " + getClass().getSimpleName());
    }
}

package com.farenda.java.spring.excludescan;

import org.springframework.stereotype.Service;

@Service
public class IncludedService {

    public IncludedService() {
        System.out.println("Instantiating " + getClass().getSimpleName());
    }
}
We want to scan the whole package and include every component except ExcludedService. In our case included beans should contain only IncludedService.

ComponentScan exclude - using annotations
To exclude some beans we can use excludeFilters on the @ComponentScan annotation like this:

package com.farenda.java.spring;

import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.EnableAutoConfiguration;
import org.springframework.context.ApplicationContext;
import org.springframework.context.annotation.*;
import org.springframework.context.annotation.ComponentScan.Filter;

import java.util.Arrays;

@ComponentScan(basePackages = "com.farenda.java.spring.excludescan",
        excludeFilters =@Filter(
                type = FilterType.REGEX,
                pattern = "com\\.farenda\\.java\\.spring\\.excludescan\\.Excluded.*"))
@EnableAutoConfiguration
public class ExcludingFromComponentScanExample {

    public static void main(String[] args) throws Exception {
        ApplicationContext context =
                SpringApplication.run(ExcludingFromComponentScanExample.class, args);

        String[] beans = context.getBeanDefinitionNames();

        // sort names only to make output more readable:
        Arrays.sort(beans);

        System.out.println("Defined beans: ");
        for (String bean : beans) {
            System.out.println(bean);
        }
    }
}
We apply REGEX FilterType that allows us nicely exclude single classes and whole packages. When we run the application you can see that only includedService is among beans in ApplicationContext built from ComponentScan:

...
 :: Spring Boot ::        (v1.2.3.RELEASE)

2015-12-20 13:08:37.601  INFO 4077 --- [           main] .f.j.s.ExcludingFromComponentScanExample
2015-12-20 13:08:37.660  INFO 4077 --- [           main] s.c.a.AnnotationConfigApplicationContext
Instantiating IncludedService
...
2015-12-20 13:08:39.292  INFO 4077 --- [           main] .f.j.s.ExcludingFromComponentScanExample : Started ExcludingFromComponentScanExample in 2.204 seconds (JVM running for 2.841)
Defined beans:
excludingFromComponentScanExample
includedService
mbeanExporter
mbeanServer
objectNamingStrategy
org.springframework.boot.autoconfigure.AutoConfigurationPackages
org.springframework.boot.autoconfigure.PropertyPlaceholderAutoConfiguration
org.springframework.boot.autoconfigure.condition.BeanTypeRegistry
org.springframework.boot.autoconfigure.jmx.JmxAutoConfiguration
org.springframework.context.annotation.ConfigurationClassPostProcessor.enhancedConfigurationProcessor
org.springframework.context.annotation.ConfigurationClassPostProcessor.importAwareProcessor
org.springframework.context.annotation.internalAutowiredAnnotationProcessor
org.springframework.context.annotation.internalCommonAnnotationProcessor
org.springframework.context.annotation.internalConfigurationAnnotationProcessor
org.springframework.context.annotation.internalRequiredAnnotationProcessor
propertySourcesPlaceholderConfigurer
2015-12-20 13:08:39.295  INFO 4077 --- [       Thread-1] s.c.a.AnnotationConfigApplicationContext : Closing org.springframework.context.annotation.AnnotationConfigApplicationContext@7a187f14: startup date [Sun Dec 20 13:08:37 CET 2015]; root of context hierarchy
2015-12-20 13:08:39.298  INFO 4077 --- [       Thread-1] o.s.j.e.a.AnnotationMBeanExporter        : Unregistering JMX-exposed beans on shutdown

Process finished with exit code 0
The same filtering mechanism can be used with includeFilters attribute, to select classes/packages that should be included in Spring ApplicationContext.

ComponentScan exclude - XML version
If you happen to still work with XML Spring Configuration, then the same thing can be done in the following way:

<context:component-scan
    base-package="com.farenda.java.spring.excludescan">

  <context:exclude-filter type="regex"
      expression="com\.farenda\.java\.spring\.excludescan\.Excluded.*"/>

</context:component-scan>

---

<h1 data-toc-skip="" style="box-sizing: border-box; margin-top: 3rem; margin-bottom: 1.5rem; font-weight: 400; line-height: 1.2; font-size: 1.9rem; color: var(--heading-color); font-family: Lato, &quot;Microsoft Yahei&quot;, sans-serif; font-style: normal; font-variant-ligatures: normal; font-variant-caps: normal; letter-spacing: normal; orphans: 2; text-align: left; text-indent: 0px; text-transform: none; widows: 2; word-spacing: 0px; -webkit-text-stroke-width: 0px; white-space: normal; background-color: rgb(255, 255, 255); text-decoration-thickness: initial; text-decoration-style: initial; text-decoration-color: initial;">Spring Constructor Injection</h1><div class="post-meta text-muted" style="box-sizing: border-box; color: rgb(108, 117, 125) !important; font-size: 0.85rem; word-spacing: 1px; font-family: &quot;Source Sans Pro&quot;, &quot;Microsoft Yahei&quot;, sans-serif; font-style: normal; font-variant-ligatures: normal; font-variant-caps: normal; font-weight: 400; letter-spacing: normal; orphans: 2; text-align: left; text-indent: 0px; text-transform: none; widows: 2; -webkit-text-stroke-width: 0px; white-space: normal; background-color: rgb(255, 255, 255); text-decoration-thickness: initial; text-decoration-style: initial; text-decoration-color: initial;"><span style="box-sizing: border-box;">Posted<span> </span><em class="" data-toggle="tooltip" data-placement="bottom" data-original-title="Mon, Jun 13, 2016 12:01 AM" title="" style="box-sizing: border-box; font-style: normal; color: var(--text-color);">Jun 13, 2016</em><span> </span></span><span style="box-sizing: border-box;"><span> </span>Updated<span> </span><em class="" data-toggle="tooltip" data-placement="bottom" data-original-title="Thu, Jun 8, 2023 11:35 AM" title="" style="box-sizing: border-box; font-style: normal; color: var(--text-color);">Jun 8, 2023</em></span><div class="d-flex justify-content-between" style="box-sizing: border-box; display: flex !important; justify-content: space-between !important;"><span style="box-sizing: border-box;">By<span> </span><em style="box-sizing: border-box; font-style: normal; color: var(--text-color);"><a href="https://twitter.com/rudaliszka" style="box-sizing: border-box; color: var(--text-color); text-decoration: none; background-color: transparent;">Przemysław Wojnowski</a></em></span><div style="box-sizing: border-box;"><span class="readtime" data-toggle="tooltip" data-placement="bottom" title="" data-original-title="380 words" style="box-sizing: border-box;"><em style="box-sizing: border-box; font-style: normal; color: var(--text-color);">2 min</em><span> </span>read</span></div></div></div><div class="post-content" style="box-sizing: border-box; font-size: 1.03rem; margin-top: 2rem; overflow-wrap: break-word; color: rgb(52, 52, 60); font-family: &quot;Source Sans Pro&quot;, &quot;Microsoft Yahei&quot;, sans-serif; font-style: normal; font-variant-ligatures: normal; font-variant-caps: normal; font-weight: 400; letter-spacing: normal; orphans: 2; text-align: left; text-indent: 0px; text-transform: none; widows: 2; word-spacing: 0px; -webkit-text-stroke-width: 0px; white-space: normal; background-color: rgb(255, 255, 255); text-decoration-thickness: initial; text-decoration-style: initial; text-decoration-color: initial;"><p style="box-sizing: border-box; margin-top: 0px; margin-bottom: 1rem;">This is one of the simplest and cleanest types of Dependency Injection in the Spring Framework. In this post we show how to use it with help of Spring annotations.</p><h2 id="spring-bean-to-inject-as-dependency" style="box-sizing: border-box; margin-top: 2.5rem; margin-bottom: 1.25rem; font-weight: 400; line-height: 1.2; font-size: 1.5rem; color: var(--heading-color); font-family: Lato, &quot;Microsoft Yahei&quot;, sans-serif;"><span class="mr-2" style="box-sizing: border-box; margin-right: 0.5rem !important;">Spring bean to inject as dependency</span><a href="https://farenda.com/spring-constructor-injection/#spring-bean-to-inject-as-dependency" class="anchor text-muted" style="box-sizing: border-box; color: rgb(108, 117, 125) !important; text-decoration: none; background-color: transparent; font-size: 19.2px; visibility: hidden; opacity: 0; transition: opacity 0.25s ease-in 0s, visibility 0s ease-in 0.25s; border-bottom: 1px solid var(--link-underline-color);"><i class="fas fa-hashtag" style="box-sizing: border-box; -webkit-font-smoothing: antialiased; display: inline-block; font-style: normal; font-variant: normal; text-rendering: auto; line-height: 1; font-family: &quot;Font Awesome 5 Free&quot;; font-weight: 900; user-select: none;"></i></a></h2><p style="box-sizing: border-box; margin-top: 0px; margin-bottom: 1rem;">Let’s specify an interface for dependency:</p><div class="language-java highlighter-rouge" style="box-sizing: border-box; border-radius: 6px; background: var(--highlight-bg-color); color: var(--highlighter-rouge-color); margin-top: 0.5rem; margin-bottom: 1.2em;"><div class="code-header" style="box-sizing: border-box; user-select: none; display: flex; justify-content: space-between; align-items: center; height: 2.25rem;"><span data-label-text="Java" style="box-sizing: border-box;"><i class="fas fa-code small" style="box-sizing: border-box; font-size: 11.536px; font-weight: 900; -webkit-font-smoothing: antialiased; display: inline-block; font-style: normal; font-variant: normal; text-rendering: auto; line-height: 1; font-family: &quot;Font Awesome 5 Free&quot;; user-select: none; margin-right: 0.4rem; color: var(--code-header-icon-color);"></i></span><button aria-label="copy" data-title-succeed="Copied!" data-original-title="" title="" style="box-sizing: border-box; border-radius: 6px; margin: 0px; font-family: inherit; font-size: inherit; line-height: inherit; overflow: visible; text-transform: none; appearance: button; cursor: pointer; border: 1px solid rgba(0, 0, 0, 0); height: 2.25rem; width: 2.25rem; padding: 0px; background-color: inherit;"><i class="far fa-clipboard" style="box-sizing: border-box; -webkit-font-smoothing: antialiased; display: inline-block; font-style: normal; font-variant: normal; text-rendering: auto; line-height: 1; font-weight: 400; font-family: &quot;Font Awesome 5 Free&quot;; user-select: none; color: var(--code-header-icon-color);"></i></button></div><div class="highlight" style="box-sizing: border-box; border-radius: 6px; background: var(--highlight-bg-color); overflow: auto; padding-top: 0.5rem; padding-bottom: 1rem;"><code style="box-sizing: border-box; font-family: SFMono-Regular, Menlo, Monaco, Consolas, &quot;Liberation Mono&quot;, &quot;Courier New&quot;, monospace; font-size: 14.42px; color: rgba(0, 0, 0, 0); overflow-wrap: break-word; hyphens: none;">

1 2 3 4 5 | package com.farenda.spring.tutorial.injection.constructor;  public interface BookRepository {     String titleById(int id); }
-- | --


</code></div></div></div>Spring Constructor Injection
Posted Jun 13, 2016  Updated Jun 8, 2023
By [Przemysław Wojnowski](https://twitter.com/rudaliszka)
2 min read
This is one of the simplest and cleanest types of Dependency Injection in the Spring Framework. In this post we show how to use it with help of Spring annotations.

Spring bean to inject as dependency
Let’s specify an interface for dependency:

package com.farenda.spring.tutorial.injection.constructor;

public interface BookRepository {
    String titleById(int id);
}
And the actual Spring Bean implementation that will be injected:

package com.farenda.spring.tutorial.injection.constructor;

import org.springframework.stereotype.Repository;

import java.util.HashMap;
import java.util.Map;

@Repository
public class InMemoryBookRepository implements BookRepository {

    // It's our local database ;-)
    private Map<Integer, String> books = new HashMap<>();

    {
        books.put(1, "Effective Java, 2nd edition");
        books.put(2, "Java Concurrency in Practice");
        books.put(3, "Spring in Action");
    }

    @Override
    public String titleById(int id) {
        return books.get(id);
    }
}
Spring component with dependency injected by constructor
Here we define another Spring Bean, but this time we are going to inject BookRepository through constructor, using @Autowired annotation:

package com.farenda.spring.tutorial.injection.constructor;

import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.stereotype.Component;

@Component
public class Library {

    private BookRepository bookRepository;

    @Autowired
    public Library(BookRepository bookRepository) {
        this.bookRepository = bookRepository;
    }

    public String findBook(int id) {
        return bookRepository.titleById(id);
    }
}
Spring resolves dependencies using argument’s type. If it finds a bean matching the type, then the bean is instantiated and injected. Else exception is thrown.

Example App using Spring Boot
Here’s the simplest Spring Boot application to run the above code:

package com.farenda.spring.tutorial.injection.constructor;

import org.springframework.boot.SpringApplication;
import org.springframework.context.ApplicationContext;
import org.springframework.context.annotation.ComponentScan;
import org.springframework.context.annotation.Configuration;

@Configuration
@ComponentScan // scan this package for Spring beans
public class ConstructorInjection {

    public static void main(String[] args) {
        ApplicationContext context = SpringApplication
                .run(ConstructorInjection.class, args);

        // Get bean from the Spring Application Context:
        Library library = context.getBean(Library.class);

        System.out.println("Title 1: " + library.findBook(1));
        System.out.println("Title 2: " + library.findBook(2));
    }
}
The above code produces the following output:

Title 1: Effective Java, 2nd edition
Title 2: Java Concurrency in Practice

---

<h1 data-toc-skip="" style="box-sizing: border-box; margin-top: 3rem; margin-bottom: 1.5rem; font-weight: 400; line-height: 1.2; font-size: 1.9rem; color: var(--heading-color); font-family: Lato, &quot;Microsoft Yahei&quot;, sans-serif;">Spring Field Injection</h1><div class="post-meta text-muted" style="box-sizing: border-box; color: rgb(108, 117, 125) !important; font-size: 0.85rem; word-spacing: 1px;"><span style="box-sizing: border-box;">Posted<span> </span><em class="" data-toggle="tooltip" data-placement="bottom" data-original-title="Tue, Jul 12, 2016 12:01 AM" title="" style="box-sizing: border-box; font-style: normal; color: var(--text-color);">Jul 12, 2016</em><span> </span></span><span style="box-sizing: border-box;"><span> </span>Updated<span> </span><em class="" data-toggle="tooltip" data-placement="bottom" data-original-title="Thu, Jun 8, 2023 11:35 AM" title="" style="box-sizing: border-box; font-style: normal; color: var(--text-color);">Jun 8, 2023</em></span><div class="d-flex justify-content-between" style="box-sizing: border-box; display: flex !important; justify-content: space-between !important;"><span style="box-sizing: border-box;">By<span> </span><em style="box-sizing: border-box; font-style: normal; color: var(--text-color);"><a href="https://twitter.com/rudaliszka" style="box-sizing: border-box; color: var(--text-color); text-decoration: none; background-color: transparent;">Przemysław Wojnowski</a></em></span><div style="box-sizing: border-box;"><span class="readtime" data-toggle="tooltip" data-placement="bottom" title="" data-original-title="389 words" style="box-sizing: border-box;"><em style="box-sizing: border-box; font-style: normal; color: var(--text-color);">2 min</em><span> </span>read</span></div></div></div><div class="post-content" style="box-sizing: border-box; font-size: 1.03rem; margin-top: 2rem; overflow-wrap: break-word;"><p style="box-sizing: border-box; margin-top: 0px; margin-bottom: 1rem; color: rgb(52, 52, 60); font-family: &quot;Source Sans Pro&quot;, &quot;Microsoft Yahei&quot;, sans-serif; font-size: 16.48px; font-style: normal; font-variant-ligatures: normal; font-variant-caps: normal; font-weight: 400; letter-spacing: normal; orphans: 2; text-align: left; text-indent: 0px; text-transform: none; widows: 2; word-spacing: 0px; -webkit-text-stroke-width: 0px; white-space: normal; background-color: rgb(255, 255, 255); text-decoration-thickness: initial; text-decoration-style: initial; text-decoration-color: initial;">This is the form of<span> </span><strong style="box-sizing: border-box; font-weight: bolder;">Dependency Injection</strong><span> </span>that requires almost no boilerplate code, contrary to setter or constructor injections. Let’s see how it works!</p><h2 id="spring-bean-to-inject-as-dependency" style="box-sizing: border-box; margin-top: 2.5rem; margin-bottom: 1.25rem; font-weight: 400; line-height: 1.2; font-size: 1.5rem; color: var(--heading-color); font-family: Lato, &quot;Microsoft Yahei&quot;, sans-serif; font-style: normal; font-variant-ligatures: normal; font-variant-caps: normal; letter-spacing: normal; orphans: 2; text-align: left; text-indent: 0px; text-transform: none; widows: 2; word-spacing: 0px; -webkit-text-stroke-width: 0px; white-space: normal; background-color: rgb(255, 255, 255); text-decoration-thickness: initial; text-decoration-style: initial; text-decoration-color: initial;"><span class="mr-2" style="box-sizing: border-box; margin-right: 0.5rem !important;">Spring bean to inject as dependency</span><a href="https://farenda.com/spring-field-injection/#spring-bean-to-inject-as-dependency" class="anchor text-muted" style="box-sizing: border-box; color: rgb(108, 117, 125) !important; text-decoration: none; background-color: transparent; font-size: 19.2px; visibility: hidden; opacity: 0; transition: opacity 0.25s ease-in 0s, visibility 0s ease-in 0.25s; border-bottom: 1px solid var(--link-underline-color);"><i class="fas fa-hashtag" style="box-sizing: border-box; -webkit-font-smoothing: antialiased; display: inline-block; font-style: normal; font-variant: normal; text-rendering: auto; line-height: 1; font-family: &quot;Font Awesome 5 Free&quot;; font-weight: 900; user-select: none;"></i></a></h2><p style="box-sizing: border-box; margin-top: 0px; margin-bottom: 1rem; color: rgb(52, 52, 60); font-family: &quot;Source Sans Pro&quot;, &quot;Microsoft Yahei&quot;, sans-serif; font-size: 16.48px; font-style: normal; font-variant-ligatures: normal; font-variant-caps: normal; font-weight: 400; letter-spacing: normal; orphans: 2; text-align: left; text-indent: 0px; text-transform: none; widows: 2; word-spacing: 0px; -webkit-text-stroke-width: 0px; white-space: normal; background-color: rgb(255, 255, 255); text-decoration-thickness: initial; text-decoration-style: initial; text-decoration-color: initial;">To start with, we’ll specify an interface for the dependency:</p><div class="language-java highlighter-rouge" style="box-sizing: border-box; border-radius: 6px; background: var(--highlight-bg-color); color: var(--highlighter-rouge-color); margin-top: 0.5rem; margin-bottom: 1.2em; font-family: &quot;Source Sans Pro&quot;, &quot;Microsoft Yahei&quot;, sans-serif; font-size: 16.48px; font-style: normal; font-variant-ligatures: normal; font-variant-caps: normal; font-weight: 400; letter-spacing: normal; orphans: 2; text-align: left; text-indent: 0px; text-transform: none; widows: 2; word-spacing: 0px; -webkit-text-stroke-width: 0px; white-space: normal; text-decoration-thickness: initial; text-decoration-style: initial; text-decoration-color: initial;"><div class="code-header" style="box-sizing: border-box; user-select: none; display: flex; justify-content: space-between; align-items: center; height: 2.25rem;"><span data-label-text="Java" style="box-sizing: border-box;"><i class="fas fa-code small" style="box-sizing: border-box; font-size: 11.536px; font-weight: 900; -webkit-font-smoothing: antialiased; display: inline-block; font-style: normal; font-variant: normal; text-rendering: auto; line-height: 1; font-family: &quot;Font Awesome 5 Free&quot;; user-select: none; margin-right: 0.4rem; color: var(--code-header-icon-color);"></i></span><button aria-label="copy" data-title-succeed="Copied!" data-original-title="" title="" style="box-sizing: border-box; border-radius: 6px; margin: 0px; font-family: inherit; font-size: inherit; line-height: inherit; overflow: visible; text-transform: none; appearance: button; cursor: pointer; border: 1px solid rgba(0, 0, 0, 0); height: 2.25rem; width: 2.25rem; padding: 0px; background-color: inherit;"><i class="far fa-clipboard" style="box-sizing: border-box; -webkit-font-smoothing: antialiased; display: inline-block; font-style: normal; font-variant: normal; text-rendering: auto; line-height: 1; font-weight: 400; font-family: &quot;Font Awesome 5 Free&quot;; user-select: none; color: var(--code-header-icon-color);"></i></button></div><div class="highlight" style="box-sizing: border-box; border-radius: 6px; background: var(--highlight-bg-color); overflow: auto; padding-top: 0.5rem; padding-bottom: 1rem;"><code style="box-sizing: border-box; font-family: SFMono-Regular, Menlo, Monaco, Consolas, &quot;Liberation Mono&quot;, &quot;Courier New&quot;, monospace; font-size: 14.42px; color: rgba(0, 0, 0, 0); overflow-wrap: break-word; hyphens: none;">

1 2 3 4 5 | package com.farenda.spring.tutorial.injection.field;  public interface BookRepository {     String titleById(int id); }
-- | --


</code></div></div><br class="Apple-interchange-newline">Spring Field Injection
Posted Jul 12, 2016  Updated Jun 8, 2023
By [Przemysław Wojnowski](https://twitter.com/rudaliszka)
2 min read
This is the form of Dependency Injection that requires almost no boilerplate code, contrary to setter or constructor injections. Let’s see how it works!

Spring bean to inject as dependency
To start with, we’ll specify an interface for the dependency:

package com.farenda.spring.tutorial.injection.field;

public interface BookRepository {
    String titleById(int id);
}
And the actual Spring Bean implementation that will be injected:

package com.farenda.spring.tutorial.injection.field;

import org.springframework.stereotype.Repository;

import java.util.HashMap;
import java.util.Map;

@Repository
public class InMemoryBookRepository implements BookRepository {

    // It's our local database ;-)
    private Map<Integer, String> books = new HashMap<>();

    {
        books.put(1, "Effective Java, 3rd edition");
        books.put(2, "Java Concurrency in Practice");
        books.put(3, "Spring in Action");
    }

    @Override
    public String titleById(int id) {
        return books.get(id);
    }
}
Spring component with dependency injected using field injection
Here we define another Spring Bean, but we are going to inject /BookRepository/ using field injection. To do that we have to annotate appropriate fields using @Autowired (or @Inject or @Resource) annotation:

package com.farenda.spring.tutorial.injection.field;

import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.stereotype.Component;

@Component
public class Library {

    @Autowired
    private BookRepository bookRepository;

    public String findBook(int id) {
        return bookRepository.titleById(id);
    }
}
It works without any setter, because underneath Spring is using reflection to inject dependencies.

Constructor or field injection
Although [constructor injection](https://farenda.com/spring/spring-constructor-injection) allows to create beans as immutable objects (fields can be marked using final modifier) and makes dependencies explicit it requires to write some boilerplate code. Because of that, in practice, field injection is used.

Example App using Spring Boot
Here’s the simplest Spring Boot application to run the above code:

package com.farenda.spring.tutorial.injection.field;

import org.springframework.boot.SpringApplication;
import org.springframework.context.ApplicationContext;
import org.springframework.context.annotation.ComponentScan;
import org.springframework.context.annotation.Configuration;

@Configuration
@ComponentScan
public class FieldInjection {

    public static void main(String[] args) {
        ApplicationContext context = SpringApplication
                .run(FieldInjection.class, args);

        Library library = context.getBean(Library.class);

        System.out.println("Title 1: " + library.findBook(1));
        System.out.println("Title 2: " + library.findBook(2));
    }
}
The above code produces the following output:

Title 1: Effective Java, 3rd edition
Title 2: Java Concurrency in Practice


---


<h1 data-toc-skip="" style="box-sizing: border-box; margin-top: 3rem; margin-bottom: 1.5rem; font-weight: 400; line-height: 1.2; font-size: 1.9rem; color: var(--heading-color); font-family: Lato, &quot;Microsoft Yahei&quot;, sans-serif; font-style: normal; font-variant-ligatures: normal; font-variant-caps: normal; letter-spacing: normal; orphans: 2; text-align: left; text-indent: 0px; text-transform: none; widows: 2; word-spacing: 0px; -webkit-text-stroke-width: 0px; white-space: normal; background-color: rgb(255, 255, 255); text-decoration-thickness: initial; text-decoration-style: initial; text-decoration-color: initial;">Spring Circular Reference - BeanCurrentlyInCreationException</h1><div class="post-meta text-muted" style="box-sizing: border-box; color: rgb(108, 117, 125) !important; font-size: 0.85rem; word-spacing: 1px; font-family: &quot;Source Sans Pro&quot;, &quot;Microsoft Yahei&quot;, sans-serif; font-style: normal; font-variant-ligatures: normal; font-variant-caps: normal; font-weight: 400; letter-spacing: normal; orphans: 2; text-align: left; text-indent: 0px; text-transform: none; widows: 2; -webkit-text-stroke-width: 0px; white-space: normal; background-color: rgb(255, 255, 255); text-decoration-thickness: initial; text-decoration-style: initial; text-decoration-color: initial;"><span style="box-sizing: border-box;">Posted<span> </span><em class="" data-toggle="tooltip" data-placement="bottom" data-original-title="Wed, Aug 10, 2016 3:01 PM" title="" style="box-sizing: border-box; font-style: normal; color: var(--text-color);">Aug 10, 2016</em><span> </span></span><span style="box-sizing: border-box;"><span> </span>Updated<span> </span><em class="" data-toggle="tooltip" data-placement="bottom" data-original-title="Thu, Jun 8, 2023 11:35 AM" title="" style="box-sizing: border-box; font-style: normal; color: var(--text-color);">Jun 8, 2023</em></span><div class="d-flex justify-content-between" style="box-sizing: border-box; display: flex !important; justify-content: space-between !important;"><span style="box-sizing: border-box;">By<span> </span><em style="box-sizing: border-box; font-style: normal; color: var(--text-color);"><a href="https://twitter.com/rudaliszka" style="box-sizing: border-box; color: var(--text-color); text-decoration: none; background-color: transparent;">Przemysław Wojnowski</a></em></span><div style="box-sizing: border-box;"><span class="readtime" data-toggle="tooltip" data-placement="bottom" title="" data-original-title="967 words" style="box-sizing: border-box;"><em style="box-sizing: border-box; font-style: normal; color: var(--text-color);">5 min</em><span> </span>read</span></div></div></div><div class="post-content" style="box-sizing: border-box; font-size: 1.03rem; margin-top: 2rem; overflow-wrap: break-word; color: rgb(52, 52, 60); font-family: &quot;Source Sans Pro&quot;, &quot;Microsoft Yahei&quot;, sans-serif; font-style: normal; font-variant-ligatures: normal; font-variant-caps: normal; font-weight: 400; letter-spacing: normal; orphans: 2; text-align: left; text-indent: 0px; text-transform: none; widows: 2; word-spacing: 0px; -webkit-text-stroke-width: 0px; white-space: normal; background-color: rgb(255, 255, 255); text-decoration-thickness: initial; text-decoration-style: initial; text-decoration-color: initial;"><p style="box-sizing: border-box; margin-top: 0px; margin-bottom: 1rem;"><strong style="box-sizing: border-box; font-weight: bolder;">BeanCurrentlyInCreationException</strong><span> </span>is thrown by<span> </span><strong style="box-sizing: border-box; font-weight: bolder;">Spring Framework</strong><span> </span>when it meets<span> </span><strong style="box-sizing: border-box; font-weight: bolder;">circular reference</strong><span> </span>while setting up application context. Here we show what is it and how to fix it!</p><h1 id="beans-with-circular-reference" style="box-sizing: border-box; margin-top: 3rem; margin-bottom: 1.5rem; font-weight: 400; line-height: 1.2; font-size: 1.9rem; color: var(--heading-color); font-family: Lato, &quot;Microsoft Yahei&quot;, sans-serif;">Beans with circular reference</h1><h2 id="bean-a-with-constructor-injected-bean-b" style="box-sizing: border-box; margin-top: 2.5rem; margin-bottom: 1.25rem; font-weight: 400; line-height: 1.2; font-size: 1.5rem; color: var(--heading-color); font-family: Lato, &quot;Microsoft Yahei&quot;, sans-serif;"><span class="mr-2" style="box-sizing: border-box; margin-right: 0.5rem !important;">Bean A with constructor injected Bean B</span><a href="https://farenda.com/spring-circular-reference-beancurrentlyincreationexception/#bean-a-with-constructor-injected-bean-b" class="anchor text-muted" style="box-sizing: border-box; color: rgb(108, 117, 125) !important; text-decoration: none; background-color: transparent; font-size: 19.2px; visibility: hidden; opacity: 0; transition: opacity 0.25s ease-in 0s, visibility 0s ease-in 0.25s; border-bottom: 1px solid var(--link-underline-color);"><i class="fas fa-hashtag" style="box-sizing: border-box; -webkit-font-smoothing: antialiased; display: inline-block; font-style: normal; font-variant: normal; text-rendering: auto; line-height: 1; font-family: &quot;Font Awesome 5 Free&quot;; font-weight: 900; user-select: none;"></i></a></h2><p style="box-sizing: border-box; margin-top: 0px; margin-bottom: 1rem;"><em style="box-sizing: border-box;">Library</em><span> </span>is a<span> </span><strong style="box-sizing: border-box; font-weight: bolder;">Spring Bean</strong><span> </span>that is using another bean -<span> </span><em style="box-sizing: border-box;">BookRepository</em><span> </span>- as a dependency<span> </span><a href="https://farenda.com/spring/spring-constructor-injection" style="box-sizing: border-box; color: var(--link-color); text-decoration: none; background-color: transparent; border-bottom: 1px solid var(--link-underline-color);">injected through constructor</a>:</p><div class="language-java highlighter-rouge" style="box-sizing: border-box; border-radius: 6px; background: var(--highlight-bg-color); color: var(--highlighter-rouge-color); margin-top: 0.5rem; margin-bottom: 1.2em;"><div class="code-header" style="box-sizing: border-box; user-select: none; display: flex; justify-content: space-between; align-items: center; height: 2.25rem;"><span data-label-text="Java" style="box-sizing: border-box;"><i class="fas fa-code small" style="box-sizing: border-box; font-size: 11.536px; font-weight: 900; -webkit-font-smoothing: antialiased; display: inline-block; font-style: normal; font-variant: normal; text-rendering: auto; line-height: 1; font-family: &quot;Font Awesome 5 Free&quot;; user-select: none; margin-right: 0.4rem; color: var(--code-header-icon-color);"></i></span><button aria-label="copy" data-title-succeed="Copied!" data-original-title="" title="" style="box-sizing: border-box; border-radius: 6px; margin: 0px; font-family: inherit; font-size: inherit; line-height: inherit; overflow: visible; text-transform: none; appearance: button; cursor: pointer; border: 1px solid rgba(0, 0, 0, 0); height: 2.25rem; width: 2.25rem; padding: 0px; background-color: inherit;"><i class="far fa-clipboard" style="box-sizing: border-box; -webkit-font-smoothing: antialiased; display: inline-block; font-style: normal; font-variant: normal; text-rendering: auto; line-height: 1; font-weight: 400; font-family: &quot;Font Awesome 5 Free&quot;; user-select: none; color: var(--code-header-icon-color);"></i></button></div><div class="highlight" style="box-sizing: border-box; border-radius: 6px; background: var(--highlight-bg-color); overflow: auto; padding-top: 0.5rem; padding-bottom: 1rem;"><code style="box-sizing: border-box; font-family: SFMono-Regular, Menlo, Monaco, Consolas, &quot;Liberation Mono&quot;, &quot;Courier New&quot;, monospace; font-size: 14.42px; color: rgba(0, 0, 0, 0); overflow-wrap: break-word; hyphens: none;">

1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20 21 22 23 | package com.farenda.spring.tutorial.injection.conflict;  import org.springframework.beans.factory.annotation.Autowired; import org.springframework.stereotype.Component;  @Component public class Library {      private BookRepository bookRepository;      @Autowired     public Library(BookRepository bookRepository) {         this.bookRepository = bookRepository;     }      public String findBook(int id) {         return bookRepository.titleById(id);     }      public String name() {         return "Public library #1";     } }
-- | --


</code></div></div></div>Spring Circular Reference - BeanCurrentlyInCreationException
Posted Aug 10, 2016  Updated Jun 8, 2023
By [Przemysław Wojnowski](https://twitter.com/rudaliszka)
5 min read
BeanCurrentlyInCreationException is thrown by Spring Framework when it meets circular reference while setting up application context. Here we show what is it and how to fix it!

Beans with circular reference
Bean A with constructor injected Bean B
Library is a Spring Bean that is using another bean - BookRepository - as a dependency [injected through constructor](https://farenda.com/spring/spring-constructor-injection):

package com.farenda.spring.tutorial.injection.conflict;

import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.stereotype.Component;

@Component
public class Library {

    private BookRepository bookRepository;

    @Autowired
    public Library(BookRepository bookRepository) {
        this.bookRepository = bookRepository;
    }

    public String findBook(int id) {
        return bookRepository.titleById(id);
    }

    public String name() {
        return "Public library #1";
    }
}
Bean B with constructor injected Bean A - circular reference
BookRepository, for some reason, want’s to have Library injected, also through constructor:

package com.farenda.spring.tutorial.injection.conflict;

import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.stereotype.Repository;

import java.util.HashMap;
import java.util.Map;

@Repository
public class BookRepository {

    private Library library;

    @Autowired
    public BookRepository(Library library) {
        this.library = library;
    }

    // It's our local database ;-)
    private Map<Integer, String> books = new HashMap<>();

    {
        books.put(1, "Effective Java, 2nd edition");
        books.put(2, "Java Concurrency in Practice");
        books.put(3, "Spring in Action");
    }

    public String titleById(int id) {
        System.out.println("In a library: " + library.name());
        return books.get(id);
    }
}
The application runner
The simplest [Spring Boot](http://farenda.com/java/spring-boot-hello-world) app to run the code:

package com.farenda.spring.tutorial.injection.conflict;

import org.springframework.boot.SpringApplication;
import org.springframework.context.ApplicationContext;
import org.springframework.context.annotation.ComponentScan;
import org.springframework.context.annotation.Configuration;

@Configuration
@ComponentScan
public class InjectionConflict {

    public static void main(String[] args) {
        ApplicationContext context = SpringApplication
                .run(InjectionConflict.class, args);

        Library library = context.getBean(Library.class);

        System.out.println("Title 2: " + library.findBook(2));
    }
}
When we run the above code the application will fail during startup with UnsatisfiedDependencyException exception, which is caused by BeanCurrentlyInCreationException:

2016-08-09 23:29:01.530  INFO 11796 --- [           main] c.f.s.t.i.conflict.InjectionConflict     : Starting InjectionConflict on namek with PID 11796 (/home/przemek/Dropbox/projekty/farenda/java/spring-tutorial/build/classes/main started by przemek in /home/przemek/Dropbox/projekty/farenda/java/spring-tutorial)
2016-08-09 23:29:01.535  INFO 11796 --- [           main] c.f.s.t.i.conflict.InjectionConflict     : No active profile set, falling back to default profiles: default
2016-08-09 23:29:01.612  INFO 11796 --- [           main] s.c.a.AnnotationConfigApplicationContext : Refreshing org.springframework.context.annotation.AnnotationConfigApplicationContext@2eda0940: startup date [Tue Aug 09 23:29:01 CEST 2016]; root of context hierarchy
2016-08-09 23:29:02.147  WARN 11796 --- [           main] s.c.a.AnnotationConfigApplicationContext : Exception encountered during context initialization - cancelling refresh attempt: org.springframework.beans.factory.UnsatisfiedDependencyException: Error creating bean with name 'bookRepository' defined in file [/home/przemek/Dropbox/projekty/farenda/java/spring-tutorial/build/classes/main/com/farenda/spring/tutorial/injection/conflict/BookRepository.class]: Unsatisfied dependency expressed through constructor argument with index 0 of type [com.farenda.spring.tutorial.injection.conflict.Library]: Error creating bean with name 'library' defined in file [/home/przemek/Dropbox/projekty/farenda/java/spring-tutorial/build/classes/main/com/farenda/spring/tutorial/injection/conflict/Library.class]: Unsatisfied dependency expressed through constructor argument with index 0 of type [com.farenda.spring.tutorial.injection.conflict.BookRepository]: Error creating bean with name 'bookRepository': Requested bean is currently in creation: Is there an unresolvable circular reference?; nested exception is org.springframework.beans.factory.BeanCurrentlyInCreationException: Error creating bean with name 'bookRepository': Requested bean is currently in creation: Is there an unresolvable circular reference?; nested exception is org.springframework.beans.factory.UnsatisfiedDependencyException: Error creating bean with name 'library' defined in file [/home/przemek/Dropbox/projekty/farenda/java/spring-tutorial/build/classes/main/com/farenda/spring/tutorial/injection/conflict/Library.class]: Unsatisfied dependency expressed through constructor argument with index 0 of type [com.farenda.spring.tutorial.injection.conflict.BookRepository]: Error creating bean with name 'bookRepository': Requested bean is currently in creation: Is there an unresolvable circular reference?; nested exception is org.springframework.beans.factory.BeanCurrentlyInCreationException: Error creating bean with name 'bookRepository': Requested bean is currently in creation: Is there an unresolvable circular reference?
2016-08-09 23:29:02.166 ERROR 11796 --- [           main] o.s.boot.SpringApplication               : Application startup failed

org.springframework.beans.factory.UnsatisfiedDependencyException: Error creating bean with name 'bookRepository' defined in file [/home/przemek/Dropbox/projekty/farenda/java/spring-tutorial/build/classes/main/com/farenda/spring/tutorial/injection/conflict/BookRepository.class]: Unsatisfied dependency expressed through constructor argument with index 0 of type [com.farenda.spring.tutorial.injection.conflict.Library]: Error creating bean with name 'library' defined in file [/home/przemek/Dropbox/projekty/farenda/java/spring-tutorial/build/classes/main/com/farenda/spring/tutorial/injection/conflict/Library.class]: Unsatisfied dependency expressed through constructor argument with index 0 of type [com.farenda.spring.tutorial.injection.conflict.BookRepository]: Error creating bean with name 'bookRepository': Requested bean is currently in creation: Is there an unresolvable circular reference?; nested exception is org.springframework.beans.factory.BeanCurrentlyInCreationException: Error creating bean with name 'bookRepository': Requested bean is currently in creation: Is there an unresolvable circular reference?; nested exception is org.springframework.beans.factory.UnsatisfiedDependencyException: Error creating bean with name 'library' defined in file [/home/przemek/Dropbox/projekty/farenda/java/spring-tutorial/build/classes/main/com/farenda/spring/tutorial/injection/conflict/Library.class]: Unsatisfied dependency expressed through constructor argument with index 0 of type [com.farenda.spring.tutorial.injection.conflict.BookRepository]: Error creating bean with name 'bookRepository': Requested bean is currently in creation: Is there an unresolvable circular reference?; nested exception is org.springframework.beans.factory.BeanCurrentlyInCreationException: Error creating bean with name 'bookRepository': Requested bean is currently in creation: Is there an unresolvable circular reference?
        at org.springframework.beans.factory.support.ConstructorResolver.createArgumentArray(ConstructorResolver.java:749) ~[spring-beans-4.2.6.RELEASE.jar:4.2.6.RELEASE]
        at org.springframework.beans.factory.support.ConstructorResolver.autowireConstructor(ConstructorResolver.java:185) ~[spring-beans-4.2.6.RELEASE.jar:4.2.6.RELEASE]
The reason is that Spring Framework first tries to instantiate all the beans and then inject them. When constructor dependency is used, Spring Framework cannot instantiate mutually dependent beans. To fix that the beans participating in circular reference have to use field/setter injection.

Field/setter injection to break constructor circular references
To fix that let’s use [field injection](https://farenda.com/spring/spring-field-injection) in the beans:

@Repository
public class BookRepository {

    @Autowired
    private Library library;

//    @Autowired
//    public BookRepository(Library library) {
//        this.library = library;
//    }

//...
}

public class Library {

    @Autowired
    private BookRepository bookRepository;

//    public Library(BookRepository bookRepository) {
//        this.bookRepository = bookRepository;
//    }

//...
}
Now Spring Framewokr can instantiate BookRepository, inject it through the constructor into the Library, and then inject it back to the BookRepository:

2016-08-09 23:55:54.594  INFO 12472 --- [           main] c.f.s.t.i.conflict.InjectionConflict     : Started InjectionConflict in 1.553 seconds (JVM running for 2.679)
In a library: Public library #1
Title 2: Java Concurrency in Practice
2016-08-09 23:55:54.605  INFO 12472 --- [       Thread-1] s.c.a.AnnotationConfigApplicationContext : Closing org.springframework.context.annotation.AnnotationConfigApplicationContext@2eda0940: startup date [Tue Aug 09 23:55:54 CEST 2016]; root of context hierarchy