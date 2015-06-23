# Unit And Integration Testing

以下是 android_guides - [Android Unit and Integration testing](https://github.com/codepath/android_guides/wiki/Android-Unit-and-Integration-testing) 的簡短整理

- Robolectric + Robotium
    - Roboletric 跑在 JVM 上，不需要特殊裝置. 適合/屬於 unit testing.
    - Robotium 需要 emulator 或真實裝置，適合/屬於 InstrumentationTest, integreation test.

## Android Testing Framework: SimpleApp Test Project

- 正常寫的 android code: ` app/src/main/java`
- Local unit tests: `app/src/test/java/folder`
- Android instrumentation test: `app/src/androidTest/java/folder`
- 情境: The first (FirstActivity) has a text field and a button. When you type in the text field and hit the button, a SecondActivity appears that displays the text entered.

### Unit testing

- Testing a particular component (i.e activity) in isolation of other components.
- JUnit: @SmallTest, @MediumTest, @LargeTest
- 例: layout 元件都存在, 不是 null; button 按下去，有產生一個 activity, 並且 intent 帶有 extras, 值也正確

### Functional Testing

- Testing a series of components (i.e activity) and their interactions with one another.
- 例: 確認 FirstActivity 中 EditText 的值 == SecondActivity 中 TextView 的值。

## Robotium

- 安裝
- Black box tests: test for expected outcomes instead of specific methods.
- `Solo` object: be used in your testXXX methods to get and set values in/from UI components and click buttons and such.
- 例: 同上面的 Functional Testing
- [Solo Actions](https://github.com/codepath/android_guides/wiki/Android-Unit-and-Integration-testing#solo-actions)

## Robolectric

- 安裝
- Mocks part of the Android framework contained in the android.jar file and which allows you to run Android tests directly on the JVM with the JUnit 4 framework. 非常適合用來跑在 CI 環境！
    - Keep in mind that Robolectric is unique in that the tests do not require an emulator to be running.
    - Fall back to a full Robotium integration test for more complex situations or multi-activity scenarios.
- `Shadow` objects: allow the code being tested to execute outside of the Android environment.
- 例: `shouldHaveButtonThatSaysAudit()`, `pressingLaunchButtonForSecondActivity()`

## Testing Comparisons 綜合評比

- Robolectric 對大部分情況很夠用了, 而且超快, 能大幅縮短 testing cycle。 但只支持 unit tests.
- Robotium 則用來測那些 Robolectric 沒辦法模擬的 Android API, 以及那些比較完整的、更像真實操作的 integration testing.
- 結論: 盡可能地用 Robolectric unit tests，用 Robotium for complete integration testing.


## 延伸: 安裝 @ Android Studio

有鑑於安裝上述的測試環境在 Android Studio 是一件麻煩事，以下有一個 github repo 跟一篇 wordpress 在講解更方便的作法。

- 文章: [Working with Robolectric and Robotium in Android Studio and Gradle](https://benwilcock.wordpress.com/2015/01/20/working-with-robolectric-and-robotium-in-android-studio-and-gradle/)
- Github repo: [benwilcock/android-alltest-gradle-sample](https://github.com/benwilcock/android-alltest-gradle-sample)
    - Robolectric, Robotium, JUnit4 and standard Android Instrumentation
