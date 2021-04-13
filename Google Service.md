​	Các dịch vụ của Google Play cung cấp một loạt các SDK trên Android để giúp bạn xây dựng ứng dụng của mình, tăng cường quyền riêng tư và bảo mật, thu hút người dùng và phát triển doanh nghiệp của bạn. Các SDK này đặc biệt ở chỗ chúng chỉ yêu cầu đưa vào ứng dụng của bạn một thư viện ứng dụng mỏng, như được minh họa trong hình 1. Trong thời gian chạy, thư viện ứng dụng giao tiếp với phần lớn quá trình triển khai của SDK và dấu ấn trong các dịch vụ của Google Play.



Bằng cách cung cấp các dịch vụ chia sẻ, triển khai phía máy khách, các dịch vụ của Google Play:

​    Giúp tối ưu hóa tài nguyên trên thiết bị, chẳng hạn như bộ nhớ và bộ nhớ, để cải thiện trải nghiệm tổng thể của người dùng.
​    Nhận các bản cập nhật tự động, không phụ thuộc vào hệ điều hành, OEM hoặc các bản cập nhật ứng dụng, người dùng của bạn sẽ nhận được các cải tiến và sửa lỗi nhanh hơn.
​    Cấp quyền cho các SDK tương thích ngược với Android 4.1 (API cấp 16), cho phép bạn tiếp cận nhiều người dùng hơn với ít nỗ lực hơn.

Cách các dịch vụ của Google Play hoạt động
SDK

Mỗi SDK được cung cấp bởi các dịch vụ của Google Play cung cấp một thư viện ứng dụng khách nhẹ chứa các API cần thiết để tương tác với dịch vụ tương ứng của nó. Các API khác cho phép bạn giải quyết bất kỳ vấn đề nào trong thời gian chạy, chẳng hạn như các dịch vụ bị thiếu, bị vô hiệu hóa hoặc lỗi thời. Nếu bạn đang sử dụng Android Studio 3.4 trở lên và bật tính năng thu nhỏ mã, trình tối ưu hóa R8 có thể giúp giảm thêm dấu vết của từng SDK và tác động của nó đối với kích thước gói ứng dụng của bạn.



Để truy cập các tính năng hoặc sản phẩm mới của dịch vụ Google Play, hãy nâng cấp SDK khi phiên bản mới được phát hành vào kho lưu trữ Google Maven.
Dịch vụ



Các dịch vụ của Google Play chứa các dịch vụ của Google trên thiết bị chạy trong nền trên mọi thiết bị Android được Google chứng nhận.



Các bản cập nhật tự động cho các dịch vụ của Google Play được phân phối độc lập với nhà cung cấp dịch vụ, hệ điều hành hoặc bản cập nhật hình ảnh hệ thống OEM. Nói chung, các thiết bị chạy Android 4.1 trở lên tự động nhận các bản cập nhật, miễn là các thiết bị này đã cài đặt các dịch vụ của Google Play và có đủ bộ nhớ. Điều này có nghĩa là người dùng nhận được các cải tiến và sửa lỗi nhanh hơn và bạn có thể tận dụng các API mới nhất trong khi tiếp cận hầu hết các thiết bị trong hệ sinh thái Android. Các thiết bị cũ hơn Android 4.1 hoặc các thiết bị không được cài đặt dịch vụ Google Play không được hỗ trợ.



## Setup

Để phát triển ứng dụng bằng cách sử dụng các API dịch vụ của Google Play, hãy thiết lập dự án của bạn với các SDK có liên quan, có sẵn từ kho lưu trữ Google maven.

Để có hướng dẫn chi tiết hơn, hãy xem trang Android Studio về cách cập nhật các công cụ SDK mà dự án ứng dụng của bạn sử dụng.

Để kiểm tra ứng dụng của bạn khi sử dụng các dịch vụ của Google Play, bạn phải sử dụng một trong các cách sau:

​    Một thiết bị Android tương thích chạy Android 4.1 (API cấp 16) trở lên và đã cài đặt ứng dụng Cửa hàng Google Play.
​    Trình giả lập Android với AVD chạy nền tảng API Google dựa trên Android 4.2.2 (API cấp 17) trở lên.



```Android
implementation 'com.google.android.gms:play-services-location:18.0.0'
```

Các phiên bản mới của SDK dịch vụ Google Play với các bản sửa lỗi và các tính năng mới được phát hành định kỳ. Các cập nhật này được thông báo trong ghi chú phát hành. Nếu ứng dụng của bạn sử dụng phần phụ thuộc đã được cập nhật, hãy thay đổi sang phiên bản mới nhất trong phần phụ thuộc của ứng dụng để tận dụng các bản sửa lỗi này.



Kiểm tra xem các dịch vụ của Google Play đã được cài đặt chưa

Như được mô tả trong phần tổng quan về các dịch vụ của Google Play, các dịch vụ của Google Play nhận các bản cập nhật tự động trên Android 4.1 (API cấp 16) trở lên thông qua ứng dụng Cửa hàng Google Play. Tuy nhiên, các thiết bị Android không có Cửa hàng Google Play sẽ không được cài đặt các dịch vụ của Google Play. Nếu ứng dụng của bạn chạy trên các thiết bị không có dịch vụ của Google Play, bạn có thể muốn kiểm tra xem các dịch vụ của Google Play đã được cài đặt trên thiết bị hay chưa trước khi bạn cố gắng sử dụng API của Google hoặc bật các tính năng trong ứng dụng của bạn yêu cầu các dịch vụ của Google Play hoạt động.

Để kiểm tra sự hiện diện của các dịch vụ Google Play trên thiết bị, hãy sử dụng phương thức isGooglePlayServicesAvailable ().

Sau đó, để bắt đầu kết nối với các dịch vụ của Google Play hoặc tìm hiểu cách phát hiện xem phiên bản dịch vụ Google Play đã cài đặt có hỗ trợ một API cụ thể hay không, hãy đọc hướng dẫn về cách Truy cập API của Google.



## Access Google APIs

Truy cập Google

Khi bạn muốn thực hiện cuộc gọi đến một trong các API trong SDK được cung cấp bởi các dịch vụ của Google Play, chẳng hạn như Google Sign-in hoặc ML Kit, trước tiên bạn cần tạo một phiên bản của đối tượng ứng dụng khách API. Các đối tượng này tự động quản lý kết nối với các dịch vụ của Google Play. Khi có kết nối, mỗi đối tượng khách API sẽ thực hiện các yêu cầu theo thứ tự. Nếu không, đối tượng khách hàng xếp hàng các yêu cầu. Trừ khi tài liệu chỉ ra cách khác, các đối tượng khách hàng rất rẻ để xây dựng; bạn có thể tạo ứng dụng API mới mỗi khi bạn muốn gọi các phương thức API.

Hướng dẫn này cho biết cách bạn có thể thực hiện lệnh gọi API tới bất kỳ SDK nào được cung cấp bởi các dịch vụ của Google Play, bao gồm cách truy cập các dịch vụ không yêu cầu ủy quyền và những dịch vụ yêu cầu ủy quyền.
Bắt đầu

Để bắt đầu, hãy thêm các công cụ và phụ thuộc cần thiết vào dự án ứng dụng của bạn, như được mô tả trong hướng dẫn về cách thiết lập các dịch vụ của Google Play.
Truy cập khi không cần ủy quyền

Để truy cập một dịch vụ không yêu cầu ủy quyền API, hãy lấy một phiên bản của đối tượng khách hàng của dịch vụ, chuyển nó vào Ngữ cảnh hiện tại hoặc Hoạt động hiện tại. Trước khi thực hiện bất kỳ lệnh gọi API nào, người dùng được nhắc nâng cấp các dịch vụ của Google Play nếu cần.

Ví dụ: để có được vị trí đã biết gần đây nhất của thiết bị bằng cách sử dụng Nhà cung cấp vị trí được kết hợp cho Android, hãy thêm logic được hiển thị trong đoạn mã sau:

```java
// Code required for requesting location permissions omitted for brevity.
FusedLocationProviderClient client =
        LocationServices.getFusedLocationProviderClient(this);

// Get the last known location. In some rare situations, this can be null.
client.getLastLocation()
        .addOnSuccessListener(this, location -> {
            if (location != null) {
                // Logic to handle location object.
            }
        });
```





Truy cập khi yêu cầu ủy quyền

Để truy cập một dịch vụ yêu cầu ủy quyền của người dùng, hãy hoàn thành các bước sau:

​    Đăng nhập người dùng.
​    Yêu cầu quyền truy cập các phạm vi mà dịch vụ yêu cầu.
​    Lấy một bản sao của đối tượng khách hàng của dịch vụ, chuyển nó vào đối tượng GoogleSignInAccount của người dùng ngoài đối tượng Ngữ cảnh hoặc Hoạt động.

Ví dụ sau triển khai việc đọc các bước hàng ngày của người dùng bằng API Google Fit. Để xem cách triển khai tương tự trong ngữ cảnh của một dự án đầy đủ, hãy xem hoạt động chính của ứng dụng BasicHistoryApiKotlin trên GitHub.



```java
public class FitFragment extends Fragment {
    private final FitnessOptions fitnessOptions = FitnessOptions.builder()
            .addDataType(DataType.TYPE_STEP_COUNT_CUMULATIVE)
            .addDataType(DataType.TYPE_STEP_COUNT_DELTA)
            .build();

    @Override
    public void onViewCreated(
            @NotNull View view, @Nullable Bundle savedInstanceState) {
        fitSignIn();
    }

    /*
     * Checks whether the user is signed in. If so, executes the specified
     * function. If the user is not signed in, initiates the sign-in flow,
     * specifying the function to execute after the user signs in.
     */
    private void fitSignIn() {
        if (oAuthPermissionsApproved()) {
            readDailySteps();
        } else {
            GoogleSignIn.requestPermissions(this, SIGN_IN_REQUEST_CODE,
                    getGoogleAccount(), fitnessOptions);
        }
    }

    private boolean oAuthPermissionsApproved() {
        return GoogleSignIn.hasPermissions(getGoogleAccount(), fitnessOptions);
    }

    /*
     * Gets a Google account for use in creating the fitness client. This is
     * achieved by either using the last signed-in account, or if necessary,
     * prompting the user to sign in. It's better to use the
     * getAccountForExtension() method instead of the getLastSignedInAccount()
     * method because the latter can return null if there has been no sign in
     * before.
     */
    private GoogleSignInAccount getGoogleAccount() {
        return GoogleSignIn.getAccountForExtension(
                requireContext(), fitnessOptions);
    }

    /*
     * Handles the callback from the OAuth sign in flow, executing the function
     * after sign-in is complete.
     */
    @Override
    public void onActivityResult(
            int requestCode, int resultCode, @Nullable Intent data) {
        super.onActivityResult(requestCode, resultCode, data);
        if (resultCode == RESULT_OK) {
            readDailySteps();
        } else {
            // Handle error.
        }
    }

    /*
     * Reads the current daily step total.
     */
    private void readDailySteps() {
        AtomicInteger total = new AtomicInteger();
        Fitness.getHistoryClient(requireContext(), getGoogleAccount())
                .readDailyTotal(DataType.TYPE_STEP_COUNT_DELTA)
                .addOnSuccessListener(dataSet -> {
                    if (!dataSet.isEmpty())
                        total.set(Integer.parseInt(dataSet.getDataPoints()
                                .get(0).getValue(FIELD_STEPS).toString()));
                        Log.i(TAG, "Total steps: $total");
                })
                .addOnFailureListener(e -> {
                    Log.w(TAG, "There was a problem getting the step count.", e);
                });
    }

    private static final int SIGN_IN_REQUEST_CODE = 1001;
}
```



## Check for API availability

Trước khi bạn bật một tính năng trong ứng dụng của mình phụ thuộc vào API dịch vụ của Google Play, hãy kiểm tra tính khả dụng của API trên thiết bị. Để làm như vậy, hãy gọi checkApiAvailable ().



```java
public Task<Location> getLastLocationIfApiAvailable(Context context) {
    FusedLocationProviderClient client =
            getFusedLocationProviderClient(context);
    return GoogleApiAvailability.getInstance()
            .checkApiAvailability(client)
            .onSuccessTask(unused -> client.getLastLocation())
            .addOnFailureListener(e -> Log.d(TAG, "Location unavailable."));
}
```

## Triển khai SDK ADMODS

- Import The Mobile Ads SDK

  ```java
  allprojects {
      repositories {
          google()
      }
  }
  ```

  ```java
  dependencies {
      implementation fileTree(dir: 'libs', include: ['*.jar'])
      implementation 'androidx.appcompat:appcompat:1.0.2'
      implementation 'com.google.android.gms:play-services-ads:20.0.0'
  }
  ```

- Cập nhật AndroidManiFest.xml

  ```java
  <manifest>
      <application>
          <!-- Sample AdMob app ID: ca-app-pub-3940256099942544~3347511713 -->
          <meta-data
              android:name="com.google.android.gms.ads.APPLICATION_ID"
              android:value="ca-app-pub-xxxxxxxxxxxxxxxx~yyyyyyyyyy"/>
      </application>
  </manifest>
  ```

  Nếu bạn chưa có ID vào link sao để get ID: https://apps.admob.com/v2/home?utm_source=internal&utm_medium=et&utm_campaign=helpcentrecontextualopt&utm_term=http%3A%2F%2Fgoo.gl%2F6Xkfcf&subid=ww-ww-et-amhelpv4

  Chọn thêm ứng dụng và  điền đẩy đủ thông tin.
  Chọn phần cài đặt ứng dụng để get id.

- ActivityMain.xml

  ```xml
    <com.google.android.gms.ads.AdView
        xmlns:ads="http://schemas.android.com/apk/res-auto"
        android:id="@+id/adView"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_centerHorizontal="true"
        android:layout_alignParentBottom="true"
        ads:adSize="BANNER"
        ads:adUnitId="ca-app-pub-3940256099942544/6300978111">
    </com.google.android.gms.ads.AdView>
  ```

- MainActivity.java

  ```java
  package ...
  
  import ...
  import com.google.android.gms.ads.AdRequest;
  import com.google.android.gms.ads.AdView;
  
  public class MainActivity extends AppCompatActivity {
      private AdView mAdView;
  
      protected void onCreate(Bundle savedInstanceState) {
          super.onCreate(savedInstanceState);
          setContentView(R.layout.activity_main);
  
          MobileAds.initialize(this, new OnInitializationCompleteListener() {
              @Override
              public void onInitializationComplete(InitializationStatus initializationStatus) {
              }
          });
  
          mAdView = findViewById(R.id.adView);
          AdRequest adRequest = new AdRequest.Builder().build();
          mAdView.loadAd(adRequest);
      }
  }
  ```

  