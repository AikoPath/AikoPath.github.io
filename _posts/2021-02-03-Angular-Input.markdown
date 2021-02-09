---
layout: post
title:  "Testing Angular Components With @Input()"
permalink: /angular_test_input_decorator/
tags: Angular Test JavaScript TypeScript
date: 19-06-2017
---

When developing an Angular (read Angular 5 or Angular 6, or whatever the current version is when you read this) component that takes an input, you might decide to unit test the whole component. At least I hope you do!

For example, we have a component, `ComponentUnderTest`, in which we want to display upcased input… I know right: what a great use-case, every business owner needs that!

So, let’s say the `ComponentUnderTest` binds and displays input.

{% highlight javascript %}
@Component({
  selector: 'component-under-test',
  template: '<div>{{ input }}</div>'
})
export class ComponentUnderTestComponent{

  @Input() input;

  processInput(): void {
    this.input = this.input.toUpperCase();
  }
}
{% endhighlight %}

To verify that `processInput()` correctly upcases our input, we can simply assign a test value to the input variable and assert that, after calling the method, the displayed input is in ALL CAPS.

Easy peasy! Right?

But by now, we need to manually call `processInput()` and until we call it, our input is still displayed in lousy lowercase.
Luckily, with Angular’s `OnInit` lifecycle hook, we can trigger our `processInput()` even before displaying anything. So let’s implement it and call `processInput()` in the corresponding method.

{% highlight javascript %}
ngOnInit(){
    this.processInput();
}
{% endhighlight %}

Let’s run the tests!

Oh no! The tests fail!

> Cannot read property ‘toUpperCase’ of undefined

Ah, of course, by the time `toUpperCase()` is called on the input in our `ngOnInit()` we have not even assigned any value to it yet.

When we actually embed our component in the production code, we would have set the value of input by binding the `input` in the component’s tag.

{% highlight javascript %}
<component-under-test input=“some input”></component-under-test>
{% endhighlight %}

So let’s embed the `ComponentUnderTest` in a `TestHostComponent`. By actually having a host or parent component, we are able to pass in exactly the input we want for our test.

In our test, we can simply define this `TestHostComponent`, include it in the testing module configuration, and instantiate it in our `beforeEach` method.

{% highlight javascript %}
describe('ComponentUnderTestComponent', () => {
  let testHostComponent: TestHostComponent;
  let testHostFixture: ComponentFixture<TestHostComponent>;

  beforeEach(async(() => {
    TestBed.configureTestingModule({
      declarations: [ComponentUnderTestComponent, TestHostComponent]
    })
      .compileComponents();
  }));

  beforeEach(() => {
    testHostFixture = TestBed.createComponent(TestHostComponent);
    testHostComponent = testHostFixture.componentInstance;
    testHostFixture.detectChanges();
  });

  it('should show TEST INPUT', () => {
    expect(testHostFixture.nativeElement.querySelector('div').innerText).toEqual('TEST INPUT');
  });

  @Component({
    selector: `host-component`,
    template: `<component-under-test input="test input"></component-under-test>`
  })
  class TestHostComponent {
  }
});
{% endhighlight %}


What results are green tests and the input is upcased at the beginning.

However, can we really be sure that the input gets upcased and that our component not just always displays “INPUT TEXT”? Let’s write another test that upcases “different test input”.

What we could do to achieve this is define another `TestHostComponent` which binds another input but we can do better than that!

{% highlight javascript %}
it('should show TEST INPUT', () => {
    testHostComponent.setInput('test input');
    testHostFixture.detectChanges();
    expect(testHostFixture.nativeElement.querySelector('div').innerText).toEqual('TEST INPUT');
});

it('should show DIFFERENT TEST INPUT', () => {
    testHostComponent.setInput('different test input');
    testHostFixture.detectChanges();
    expect(testHostFixture.nativeElement.querySelector('div').innerText).toEqual('DIFFERENT TEST INPUT');
});
@Component({
    selector: `host-component`,
    template: `<component-under-test [input]="input"></component-under-test>`
})
class TestHostComponent {
    private input: string;

    setInput(newInput: string) {
        this.input = newInput;
    }
}
{% endhighlight %}


`setInput()` sets the input in our host component. Assigning the input in our test before we let Angular detect the changes allows both our tests to pass..

Now, imagine we have to bind not only one but multiple inputs to our component. Do we now need to write a setter method for each input?

Luckily, the answer is no!

{% highlight javascript %}
it('should show DIFFERENT TEST INPUT', () => {
    testHostComponent.componentUnderTestComponent.input = 'different test input';
    testHostFixture.detectChanges();
    expect(testHostFixture.nativeElement.querySelector('div').innerText).toEqual('DIFFERENT TEST INPUT');
});
@Component({
    selector: `host-component`,
    template: `<component-under-test></component-under-test>`
})
class TestHostComponent {
    @ViewChild(ComponentUnderTestComponent)
    public componentUnderTestComponent: ComponentUnderTestComponent;
}
{% endhighlight %}


Instead of having a setter at all, we can also get a reference to our component from within the host component and pass it into our test. There we have full control over our component and can modify any field we want.

---

### Summary

* To test components that bind an input via the `@Input()` decorator, we can create a host component in our test to wrap our test component.
* For multiple test inputs, we can add a setter to our host component.
* For more that one input binding and even more control over our component under test, we can grab it from within the host component with `@ViewChild` and pass it into our test directly.

Complete source code can be found on [GitHub](https://github.com/AikoPath/ComponentInputTest).

(This article has been featured in the book [Angular for Enterprise-Ready Web Applications](https://books.google.com.sg/books?id=9YLoDwAAQBAJ&pg=PA642&lpg=PA642&dq=aiko+klostermann&source=bl&ots=fCh5YzESYT&sig=ACfU3U2q1ehyaOUNPRa_FtkhzAHgCMNgqQ&hl=en&sa=X&ved=2ahUKEwjz3qT1msXqAhXEWisKHRC4AOs4ChDoATADegQIChAB#v=onepage&q=aiko%20klostermann&f=false) by Doguhan Uluca)
