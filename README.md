# Learning ReactHooks

Hãy cùng tìm hiểu về ReactHooks thông qua các vấn đề và ví dụ cụ thể

Các lệnh để chạy dự án lên:

```
 npm start
```

## 00-Bản mẫu

Chúng ta cần tạo một tệp index.js để khởi tạo mã và một tệp demo.js để thực hiện các vấn đề cần giải quyết.

#### index.js

```jsx
import React from "react";
import ReactDOM from "react-dom";
import { MyComponent } from "./demo";
import "./styles.css";

function App() {
  return (
    <div className="App">
      <MyComponent />
    </div>
  );
}

const rootElement = document.getElementById("root");
ReactDOM.render(<App />, rootElement);
```

### demo.js

```jsx
import React from "react";

export const MyComponent = (props) => {
  return <h2>My Component</h2>;
};
```

## 01-useState()

Trong mẫu cơ bản này, chúng ta sẽ chỉ thêm trạng thái vào một thành phần hàm, bằng cách sử dụng _React.useState_

- Nếu thay đổi một giá trị nào đó nó sẽ nhận giá trị thay đổi và set lại dùng thích hợp cho việc cập nhật lại dữ liệu của một đối tượng, cập nhật lại dữ liệu là chuỗi hoặc số ,...
- Ví dụ:

```jsx
import React from "react";

export const MyComponent = (props) => {
  const [myName, setMyName] = React.useState("John Doe");

  return (
    <>
      <h4>{myName}</h4>
      <input value={myName} onChange={(e) => setMyName(e.target.value)} />
    </>
  );
};
```

- Trong ví dụ trên khi ta nhập một giá trị mới vào trong thẻ input thì việc cần làm đối với useState là tại hàm onChange ta chỉ việc lấy giá trị từ input từ phương thức e.target.value và truyền vào setState cụ thể trong ví dụ là:

```diff
 setMyName(e.target.value)
```

- Lưu ý khi dùng useState nếu bạn muốn set giá trị ban đầu cụ thể cho một state thì bạn có thể truyền vào useState() như trên ví dụ.

```diff
...React.useState('John Doe');
```

- Khi sử dụng useState để cập nhật đổi tượng cũng tương tự cụ thể ta có ví dụ:

```jsx
import React from "react";

export const MyComponent = (props) => {
  const [userInfo, setUserInfo] = React.useState({
    name: "John",
    lastname: "Doe",
  });
  return (
    <>
      <h4>
        {userInfo.name}
        {userInfo.lastname}
      </h4>
      <input
        value={userInfo.name}
        onChange={(e) =>
          setUserInfo({
            ...userInfo,
            name: e.target.value,
          })
        }
      />
      <input
        value={userInfo.lastname}
        onChange={(e) =>
          setUserInfo({
            ...userInfo,
            lastname: e.target.value,
          })
        }
      />
    </>
  );
};
```
