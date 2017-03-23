# RX-Binding
A library implementation for faster binding of android views with observables. Uses rxjava 1.x and rxandroid 1.x dependencies

## About RX Binding
RX Binding is a library developed by Jake Wharton for faster Android UI widgets binding.
RxJava binding APIs for Android UI widgets from the platform and support libraries.

In this repo I had made the same form validation but using RX binding library for binding andrioid UI widgets to observables.
 
```
It removes all boiler plate code
Observable<CharSequence> emailObservable = RxTextView.textChanges(email);
```
That’s it. You now have an observable ready to use.
![](https://www.dropbox.com/s/3smlmlab9yb9670/device-2017-03-23-235441.gif?raw=1)

```
//its so easy to make a subscription now
_subscription = Observable.combineLatest(emailObservable, usernameObservable,
                /*Note that here in Func3 we have 3 strings which are events emitted from observable strings
                * and we are here combining three strings into a boolean observable
                *which is subscribed to an action Action1 which gives instruction to submit button
                * */
                phoneObservable, new Func3<CharSequence, CharSequence, CharSequence, Boolean>() {
                    @Override
                    public Boolean call(CharSequence email, CharSequence username, CharSequence phone) {
                        Log.i(TAG, "email: " + email + ", username: " + username + ", phone: " + phone);
                        return false;
                    }
                }).subscribe(new Action1<Boolean>() {
            @Override
            public void call(Boolean aBoolean) {
                Log.i(TAG, "submit button enabled: " + aBoolean);
            }
});
```

## Authors

* **Pranav Gupta**

## License

This project is licensed under the MIT License

## Acknowledgments

RX Binding provided by Jake Wharton


