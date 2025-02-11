### **Interacting with AWS là gì?**  
**Interacting with AWS** có nghĩa là tương tác hoặc giao tiếp với các dịch vụ AWS bằng nhiều cách khác nhau để quản lý, triển khai và vận hành hệ thống trên AWS Cloud.  

---

### **1. Các cách tương tác với AWS**  

AWS cung cấp nhiều phương thức để người dùng có thể tương tác với các dịch vụ:  

#### ✅ **1.1 AWS Management Console (Giao diện web)**
- **Giao diện đồ họa (GUI)** giúp quản lý tài nguyên AWS một cách trực quan.  
- Phù hợp cho người mới bắt đầu hoặc khi cần thao tác nhanh.  
- Ví dụ: Tạo EC2, S3, RDS chỉ với vài cú click chuột.  

#### ✅ **1.2 AWS Command Line Interface (AWS CLI)**
- Dùng lệnh trên terminal để quản lý AWS.  
- Hỗ trợ tự động hóa và scripting.  
- Ví dụ:  
  ```bash
  aws s3 ls
  aws ec2 describe-instances
  aws lambda invoke --function-name myLambdaFunction output.json
  ```  

#### ✅ **1.3 AWS SDKs (Software Development Kits)**
- Cung cấp thư viện để tương tác với AWS bằng các ngôn ngữ lập trình như **Node.js, Python, Java, Go, .NET**...  
- Ví dụ với **AWS SDK for JavaScript (Node.js)**:  
  ```typescript
  import { S3Client, PutObjectCommand } from "@aws-sdk/client-s3";

  const s3 = new S3Client({ region: "us-east-1" });

  async function uploadFile(bucket: string, key: string, body: Buffer) {
    await s3.send(new PutObjectCommand({ Bucket: bucket, Key: key, Body: body }));
    console.log("File uploaded successfully");
  }
  ```  

#### ✅ **1.4 AWS CloudFormation & AWS CDK**
- **AWS CloudFormation**: Dùng YAML/JSON để định nghĩa và triển khai hạ tầng như code (IaC - Infrastructure as Code).  
- **AWS CDK (Cloud Development Kit)**: Dùng TypeScript, Python, Java để viết mã định nghĩa hạ tầng thay vì YAML.  
- Ví dụ với **AWS CDK (TypeScript)** để tạo một S3 Bucket:  
  ```typescript
  import * as cdk from "aws-cdk-lib";
  import * as s3 from "aws-cdk-lib/aws-s3";

  class MyStack extends cdk.Stack {
    constructor(scope: cdk.App, id: string) {
      super(scope, id);
      new s3.Bucket(this, "MyBucket");
    }
  }

  const app = new cdk.App();
  new MyStack(app, "MyStack");
  ```  

#### ✅ **1.5 AWS API Gateway & REST API**
- AWS cung cấp **REST API** và **GraphQL API** để ứng dụng bên ngoài gọi đến các dịch vụ AWS.  
- Ví dụ: Gửi request đến AWS API Gateway bằng `curl`:
  ```bash
  curl -X GET https://your-api-id.execute-api.us-east-1.amazonaws.com/prod/resource
  ```

---

### **2. Khi nào sử dụng cách nào?**  
| Cách tiếp cận | Khi nào sử dụng? |
|--------------|----------------|
| **AWS Console** | Khi muốn thao tác nhanh bằng giao diện web. |
| **AWS CLI** | Khi cần tự động hóa, scripting, thao tác nhanh. |
| **AWS SDK** | Khi lập trình ứng dụng cần tích hợp AWS. |
| **AWS CloudFormation/CDK** | Khi triển khai hạ tầng bằng code (IaC). |
| **AWS API Gateway** | Khi cần gọi AWS từ hệ thống bên ngoài. |
