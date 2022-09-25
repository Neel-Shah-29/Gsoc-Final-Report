# Final Evaluation Report for GSOC 2022

<div align="center">
<img src="https://user-images.githubusercontent.com/84740927/170821829-f631f5f7-c410-429a-acdc-d9cc81d13dd3.jpeg" alt="drawing" width="500"/>
</div> 


## Details

|  |  |
| --- | --- |
| Name | [Neel Shah](https://github.com/Neel-Shah-29) |
| Organisation | [CERN HSF (Root Project)](https://www.fz-juelich.de/en) |
| Mentor | [Dr. Lorenzo Moneta](https://github.com/lmoneta) |
| Project | [ROOT - TMVA SOFIE Developments - Inference Code Generation for Deep Learning models](https://summerofcode.withgoogle.com/programs/2022/projects/vEuHzl6G) |

### Proposal Link :- [Inference Code Generation for Deep Learning models](https://docs.google.com/document/d/1tvTY9Rq5j0XW8KFfvkWHWlmE__-94h-Nj0tCkMjYnzs/edit?usp=sharing)

## Pre-GSOC Period
Getting into GSOC was my dream since college years, On May 20, i was so delighted when i got into my preferred Project into one of the most competitive Organisations.I will forever remember those sleepless nights spent in solving those tasks, debugging, building the project !!
I have prepared a detailed blog on how did i got into GSOC 2022 at CERN HSF in detail [here](https://gist.github.com/Neel-Shah-29/3f04f05a8a353605068e32e55a5093c1)


## Community Bonding Period

<div align="center">
<img src="https://miro.medium.com/max/1200/1*YvvzCmO4dbCPeTPOq7_OKA.png" alt="drawing" width="500"/>
</div>

This is the period of time between when accepted GSoC contributors are announced and the time they are expected to start coding. This time is an excellent one to introduce your GSoC contributors to the community, get them on the right mailing lists, introduce them to the codebase, discuss how they will work with their mentors on their timeline for the program, etc.

Again I have written a very detailed blog on Community Bonding Period [here](https://gist.github.com/Neel-Shah-29/b2c887adaa118ba68b42e324d3b2a47a).

### Brief Description of Work Done:-

- For TMVA projects we usually have weekly meetings to discuss about the projects and solve the difficulties of everyone. So attending those meetings are mandatory as it involves your communication with other gsoc students of TMVA. Also the round table discussion solves all queries which you have as all the students and mentors give solutions and guidelines on it. Additionally we can also set a meeting with the mentor if required.

- In TMVA projects, we have a specific idea of presenting our projects with the detailed timeline of implementation in front of mentors and other Gsoc students so we can get familier with other's project as well and by that time our concrete strategy of project is also ready.

  Here is my presentation for reference:- [Inference Code Generation for Deep Learning models](https://docs.google.com/presentation/d/1bl1Xk5esr5TJEHKoro7o05pRQ2J997Qb1hc68XfU_0s/edit?usp=sharing)

- I built and set up the Root environment in my laptop as required. [Here](https://root.cern/install/build_from_source/) is the link to build Root from source.

- Finalised the evaluation dates so that i get enough time to complete my long term project. I chose a 16 weeks project after discussing with the mentor as my college reopens from July 18 and i will get less time to devote after that. 

- Lastly, I began coding part for one of the easy operator which is Leaky Relu so i get an headstart for the Project. Here is the link to the PR :- https://github.com/root-project/root/pull/10415

**Pro-Tip** :- Use this Period very well to connect with your mentors, other Gsoc Candidates and the organisation as a whole!

## Flowchart to Generate the Code in SOFIE
![Untitled Diagram drawio(2)](https://user-images.githubusercontent.com/84740927/192113032-1fbe4f4f-fcb9-4974-8878-ed85b97c69f8.png)

## Coding Period 

The first 3 PRs were implemented in the Community Bonding Period. 

#### 1) Fixed a bug related to build in RModelParser_ONNX.cxx ( when building in Ubuntu 20.04)
![image](https://user-images.githubusercontent.com/84740927/159856024-8b399e36-d835-4726-b6dc-9d1a5b90dbc3.png)

The above bug was noticed by me when i was building Root on my local computer. This can be resolved by just removing example_outputs argument from PyRunString function.

- **PR Status**:-

| Pull Request| PR Number |   Status     |
| :---        |    :----:   |          ---: |
| Fix error related to build | [#10223](https://github.com/root-project/root/pull/10223)       | <img src="https://img.shields.io/badge/PR-Merged-blueviolet?style=for-the-badge&logo=appveyor"> |

#### 2) Fixed some spelling Errors and indentation issues in the operators.

There were some speling errors and indentation issues in some operators like Pool, Conv, Reshape, Slice, Batch Normalization, Add and Gemm. I fixed them in these 2 PRs.

- **PR Status**:-

| Pull Request| PR Number |   Status     |
| :---        |    :----:   |          ---: |
| Indentation and spelling Errors fixed | [#10435](https://github.com/root-project/root/pull/10435)       | <img src="https://img.shields.io/badge/PR-Merged-blueviolet?style=for-the-badge&logo=appveyor"> |
| Indentation and spelling Errors fixed | [#10342](https://github.com/root-project/root/pull/10342)       | <img src="https://img.shields.io/badge/PR-Merged-blueviolet?style=for-the-badge&logo=appveyor"> |

#### 3) I have also contributed to fusing of Add and the MatMul operators in a Gemm Operator
Now our task is to Implement the capability to parse the MatMul and Add operators together and fuse them in a Gemm operator in the TMVA SOFIE parser (RModelParser_ONNX.cxx) .
So basically we take  the data of  MatMul operator and if we get Add operator exactly after the MatMul operator , we fuse both the Add and the MatMul operators and give their data to Gemm operator. Gemm operator is explained [here](https://petewarden.com/2015/04/20/why-gemm-is-at-the-heart-of-deep-learning/) in detail.
This improvement was added by my mentor Lorenzo Moneta in his PR , the link to my commit can be found [here](https://github.com/root-project/root/pull/10315/commits/fda26827ecfc76c23b2e4b634d8cf54c5cabf8dc).

#### 4) Finalise the **Leaky Relu PR** which was sent during Community Bonding Period. 
I have written a detailed blog for the Leaky Relu Operator implementation as well. [Here](https://gist.github.com/Neel-Shah-29/f0371566ca1e24a6b3a9b4097cdd44db) you can find the detailed description of the Operator.
Here, I will provide a breif Description about it.

- **Defination** :- [Leaky Relu ONNX Documentation](https://github.com/onnx/onnx/blob/main/docs/Operators.md#LeakyRelu)

- **Code snippet of Implementation** :-
```C++
   std::string Generate(std::string OpName){
      OpName = "op_" + OpName;
      if (fShape.empty()) {
         throw std::runtime_error("TMVA SOFIE Transpose Leaky Relu called to Generate without being initialized first");
      }
      std::stringstream out;
      size_t length = ConvertShapeToLength(fShape);

      out << SP << "float " << OpName << "_alpha = " << std::setprecision(std::numeric_limits<float>::max_digits10) << falpha << ";\n";

      out << "\n//------ LEAKY RELU\n";
      out << SP << "for (int id = 0; id < " << length << " ; id++){\n";
      out << SP << SP << "tensor_" << fNY << "[id] = ((tensor_" << fNX << "[id] > 0 )? tensor_" << fNX << "[id] : "<< OpName << "_alpha * tensor_"<< fNX<<"[id]);\n";
      out << SP << "}\n";
      return out.str();
   }
```

- Fix warning related to length in compiled code when there are no initialized tensors
```
build/build/tmva/sofie/test/LinearWithLeakyRelu_FromONNX.hxx:24:8: warning: unused variable ‘length’ [-Wunused-variable]
```
It was general for all SOFIE operators not having a weight tensor. It is resolved by applying a small fix, we directly return when the tensors are not initialized.

``` if (fInitializedTensors.empty()) return;```

- **PR Status**:-

| Pull Request| PR Number |   Status     |
| :---        |    :----:   |          ---: |
| Leaky Relu ONNX Operator | [#10415](https://github.com/root-project/root/pull/10415)       | <img src="https://img.shields.io/badge/PR-Merged-blueviolet?style=for-the-badge&logo=appveyor"> |

#### 5) Fix the implementation of **Max Pool ONNX Operator for 1D and 3D cases.**

- **Defination** :- [Max-Pool ONNX Documentation](https://github.com/onnx/onnx/blob/main/docs/Operators.md#MaxPool)

- MaxPool ONNX Operator was only supported for the 2D case, i.e 4d tensors but i need to extend its support for the 1D and 3D cases as well.

- Earlier it was giving a runtime error for 1d and 3d cases of Max Pool operator.

- Error is described in the image mentioned below.

![image](https://user-images.githubusercontent.com/84740927/180577234-b23267c8-12b0-4970-a730-e22755fc0dcb.png)

- I also added the Unit Tests for MaxPool 1D, MaxPool 2D, MaxPool 3D and the Average Pool Operators.

- **PR Status**:-

| Pull Request| PR Number |   Status     |
| :---        |    :----:   |          ---: |
| Max Pool ONNX Operator | [#10768](https://github.com/root-project/root/pull/10768)       | <img src="https://img.shields.io/badge/PR-Merged-blueviolet?style=for-the-badge&logo=appveyor"> |



#### 6) Implemented all the 4 Basic Binary Operators:- Add,Sub,Mul and Div with the corresponding Unit Tests.

- **Defination** :- 
 1. [Add ONNX Documentation](https://github.com/onnx/onnx/blob/main/docs/Operators.md#Add)
 2. [Sub ONNX Documentation](https://github.com/onnx/onnx/blob/main/docs/Operators.md#Sub)
 3. [Mul ONNX Documentation](https://github.com/onnx/onnx/blob/main/docs/Operators.md#Mul)
 4. [Div ONNX Documentation](https://github.com/onnx/onnx/blob/main/docs/Operators.md#Div)
 
 - I have implemented the four Basic Binary operators in a single file, they all are declared in an enum and we have used Type traits for making the code more modular and reusable. Below is the code sample for the same.

```C++
enum EBasicBinaryOperator { Add, Sub, Mul, Div };

template <typename T, EBasicBinaryOperator Op1>
struct BinaryOperatorTrait {
   const char *Name() { return ""; }
   const char *Op() { return ""; }
};
template <typename T>
struct BinaryOperatorTrait<T, Add> {
   static const char *Name() { return "Add"; }
   static std::string Op(const std::string &t1, const std::string t2) { return t1 + " + " + t2; }
};

template <typename T>
struct BinaryOperatorTrait<T, Sub> {
   static const char *Name() { return "Sub"; }
   static std::string Op(const std::string &t1, const std::string t2) { return t1 + " - " + t2; }
};

template <typename T>
struct BinaryOperatorTrait<T, Mul> {
   static const char *Name() { return "Mul"; }
   static std::string Op(const std::string &t1, const std::string t2) { return t1 + " * " + t2; }
};

template <typename T>
struct BinaryOperatorTrait<T, Div> {
   static const char *Name() { return "Div"; }
   static std::string Op(const std::string &t1, const std::string t2) { return t1 + " / " + t2; }
};
```

Now in the `Generate` function we implement the defination of operators, since we used the traits we just need to perform the operations between the 2 tensors using `BinaryOperatorTrait<T,Op>::Op()`

```C++
std::string Generate(std::string OpName)
   {
      OpName = "op_" + OpName;

      if (fShape.empty()) {
         throw std::runtime_error("TMVA SOFIE Binary Op called to Generate without being initialized first");
      }
      std::stringstream out;
      size_t length = ConvertShapeToLength(fShape);
      out << "\n//------ " + std::string(BinaryOperatorTrait<T, Op>::Name()) + "\n";
      out << SP << "for (size_t id = 0; id < " << length << " ; id++){\n";
      out << SP << SP << "tensor_" << fNY
          << "[id] = " +
                std::string(BinaryOperatorTrait<T, Op>::Op("tensor_" + fNX1 + "[id]", "tensor_" + fNX2 + "[id]")) +
                " ;\n";
      out << SP << "}\n";
      return out.str();
   }

};
```

- I also implemented the **Multi-Directional Broadcasting** for SOFIE.

The following is the algorithm and its implemented in the SOFIE_common.cxx.
    
CASE-1:-The tensors all have exactly the same shape. : We support it already now

CASE-2:-The tensors all have the same number of dimensions and the length of each dimensions is either a common length or 1.
**Example:-** This is the example for two tensors as (2,3,4)  and (1,3,4) the result is (2,3,4)  

CASE-3:- The tensors that have too few dimensions can have their shapes prepended with a dimension of length 1 to satisfy CASE-2. **Example:-** This is the case for (3,4,5) and (2,1,1,1). Here we transform first tensor to (1,3,4,5) and the is like case 2 above. The result is (2,3,4,5)

So the algorithm should do: 
```
CASE-1:- Check if tensor have same shape - nothing special to do, we already supported it.

CASE-2 and CASE-3 :- If shape is different we call the multi-directional broadcasting function.

CASE-3 :- if shapeA .size() < shapeB.size() we insert in the shape vector values of 1 at the beginning of the tensor until shapeA.size() == shapeB.size()
CASE-2 :- We look then to the shape values, and if they are equal result is same, if shapeA[i] not equal to shapeB[i] we have the result shape equal to shapeA[i] if shapeB[i] = 1 or shapeB[i] if shapeA[i] = 1.
```

Code Snippet implementing Multi-Directional Broadcasting.
```C++
std::vector<size_t>  UTILITY::Multidirectional_broadcast(std::vector<size_t> input1_shape, std::vector<size_t> input2_shape)
{
   std::vector<size_t> input_shape = (input1_shape.size() > input2_shape.size())?input1_shape:input2_shape;
   std::vector<size_t> output_shape(input_shape);
   
   if(input1_shape.size() < input2_shape.size()){
   // Check if input1_shape.size() < input2_shape.size() we insert in the shape vector values of 1 at the beginning of the tensor until input1_shape.size() == input2_shape.size()
      auto it = input1_shape.begin();
      while (input1_shape.size() < input2_shape.size()) {
         it = input1_shape.insert(it, 1);
      }
   }
   else if(input2_shape.size() < input1_shape.size()){
   // Check if input2_shape.size() < input1_shape.size() we insert in the shape vector values of 1 at the beginning of the tensor until input1_shape.size() == input2_shape.size()
      auto it = input2_shape.begin();
      while (input2_shape.size() < input1_shape.size()) {
         it = input2_shape.insert(it, 1);
      }
   }
      //check if both the input have same shape, nothing to do directly return the output_shape as the same shape.
   if(input1_shape.size() == input2_shape.size()){
      if(input1_shape != input2_shape){
         //Check the shape values, if input1[i] not equal to input2[i] we have the result shape equal to input1[i] if input2[i] = 1 or viceversa
         for(size_t j = 0; j < input1_shape.size() ; j++){
            if(input1_shape[j] == input2_shape[j]){
               output_shape[j] = input1_shape[j];
            }
            else if(input1_shape[j] > input2_shape[j] && input2_shape[j] == 1){
               output_shape[j] = input1_shape[j];
            }
            else if(input2_shape[j] > input1_shape[j] && input1_shape[j] == 1){
               output_shape[j] = input2_shape[j];
            }
         }
      }

   }
   return output_shape;

}
```

- **PR Status**:-

| Pull Request| PR Number |   Status     |
| :---        |    :----:   |          ---: |
| Basic Binary ONNX Operator | [#10822](https://github.com/root-project/root/pull/10822)       | <img src="https://img.shields.io/badge/PR-Merged-blueviolet?style=for-the-badge&logo=appveyor"> |

#### 7) Implemented the Tanh ONNX operator with the corresponding unit tests.

- **Defination:-** [Tanh ONNX Documentation](https://github.com/onnx/onnx/blob/main/docs/Operators.md#Tanh)

- Code demonstrating the implementation of Tanh function in the `Generate` function.
```C++
std::string Generate(std::string OpName){
      OpName = "op_" + OpName;
      if (fShape.empty()) {
         throw std::runtime_error("TMVA SOFIE Transpose Tanh called to Generate without being initialized first");
      }
      std::stringstream out;
      size_t length = ConvertShapeToLength(fShape);
      out << "\n//------ TANH\n";
      out << SP << "for (int id = 0; id < " << length << " ; id++){\n";
      out << SP << SP << "tensor_" << fNY << "[id] = std::tanh(tensor_" << fNX << "[id]);\n";
      out << SP << "}\n";
      return out.str();
   }
```

- For tanh activation function we require `cmath` library to support the tanh operator. So we add the required libraries in `RModelParser_ONNX.cxx` in the Parse method.
```C++
  if (op_type == "Tanh")
    rmodel.AddNeededStdLib("cmath");
```

- **PR Status**:-

| Pull Request| PR Number |   Status     |
| :---        |    :----:   |          ---: |
| Tanh ONNX Operator | [#10913](https://github.com/root-project/root/pull/10913)       | <img src="https://img.shields.io/badge/PR-Merged-blueviolet?style=for-the-badge&logo=appveyor"> |

#### 8) Implemented the Neg ONNX operator with the corresponding unit tests.

- **Defination:-** [Neg ONNX Documentation](https://github.com/onnx/onnx/blob/main/docs/Operators.md#Neg)

- Code demonstrating the implementation of Tanh Operator in the `Generate` function.
```C++
std::string Generate(std::string OpName){
      OpName = "op_" + OpName;
      if (fShape.empty()) {
         throw std::runtime_error("TMVA SOFIE Neg Op called to Generate without being initialized first");
      }
      std::stringstream out;
      size_t length = ConvertShapeToLength(fShape);

      out << "\n//------ Neg\n";
      out << SP << "for (int id = 0; id < " << length << " ; id++){\n";
      out << SP << SP << "tensor_" << fNY << "[id] = ((-1)*(tensor_" << fNX << "[id]));\n";
      out << SP << "}\n";
      return out.str();
   }
```

- **PR Status**:-

| Pull Request| PR Number |   Status     |
| :---        |    :----:   |          ---: |
| Neg ONNX Operator | [#10946](https://github.com/root-project/root/pull/10946)       | <img src="https://img.shields.io/badge/PR-Merged-blueviolet?style=for-the-badge&logo=appveyor"> |

#### 9) Implemented the Pow ONNX Operator

- **Defination:-** [Pow ONNX Documentation](https://github.com/onnx/onnx/blob/main/docs/Operators.md#Pow)

- Code demonstrating the implementation of Pow Operator, It is included as one of the Basic Binary Operator.
```C++
enum EBasicBinaryOperator { Add, Sub, Mul, Div, Pow };

template <typename T, EBasicBinaryOperator Op1>
struct BinaryOperatorTrait {
   const char *Name() { return ""; }
   const char *Op() { return ""; }
};
template <typename T>
struct BinaryOperatorTrait<T, Pow> {
   static const char *Name() { return "Pow"; }
   static std::string Op(const std::string &t1, const std::string t2) { return "std::pow(" + t1 + "," + t2 + ")"; }
};
```

I have implemented the multi-directional broadcasting for broadcasting the shapes of output tensors. Currently its only supported for input and output tensors having same length.
```C++
   void Initialize(RModel &model)
   {
      // input must be a graph input, or already initialized intermediate tensor
      if (model.CheckIfTensorAlreadyExist(fNX1) == false) {
         throw std::runtime_error(std::string("TMVA SOFIE Binary Op Input Tensor ") + fNX1 + "is not found in model");
      }
      if (model.CheckIfTensorAlreadyExist(fNX2) == false) {
         throw std::runtime_error(std::string("TMVA SOFIE Binary Op Input Tensor ") + fNX2 + "is not found in model");
      }
      auto shapeX1 = model.GetTensorShape(fNX1);
      auto shapeX2 = model.GetTensorShape(fNX2);
      // If the shape of 2 tensors are not same we perform multi-directional Broadcasting.
      // We only support tensors with same length and the resultant output length should also be same.
      if (shapeX1 != shapeX2) {
         fShape = UTILITY::Multidirectional_broadcast(shapeX1, shapeX2);
         size_t length1 = ConvertShapeToLength(shapeX1);
         size_t length2 = ConvertShapeToLength(shapeX2);
         size_t output_length = ConvertShapeToLength(fShape);
         if (length1 != length2 || length1 != output_length) {
            throw std::runtime_error(
               std::string("TMVA SOFIE Binary Op does not support input tensors with different lengths. The output "
                           "tensor should also have the same length as the input tensors."));
         }
      }
      // If both the tensors have same shape then assign the same shape to resultant output.
      else if (shapeX1 == shapeX2) {
         fShape = shapeX1;
      }
      model.AddIntermediateTensor(fNY, model.GetTensorType(fNX1), fShape);
   }
```
- **PR Status**:-

| Pull Request| PR Number |   Status     |
| :---        |    :----:   |          ---: |
| Pow ONNX Operator | [#10971](https://github.com/root-project/root/pull/10971)       | <img src="https://img.shields.io/badge/PR-Merged-blueviolet?style=for-the-badge&logo=appveyor"> |

#### 10) Implemented the Cast ONNX Operator

- **Defination:-** [Cast ONNX Documentation](https://github.com/onnx/onnx/blob/main/docs/Operators.md#Cast)

- First SOFIE was only supporting `ETensorType::FLOAT` input and output tensors now the code was implemented so that it can support for other datatypes as well like `ETensorType::INT16`, `ETensorType::INT32`, `ETensorType::INT64`, `ETensorType::UINT16`, `ETensorType::UINT32`, `ETensorType::UINT64` and `ETensorType::DOUBLE`.

- Code Snippet demonstrating the implementation of Cast Operator in `Generate` function.

```C++
std::string Generate(std::string OpName){
      OpName = "op_" + OpName;
      if (fShape.empty()) {
         throw std::runtime_error("TMVA SOFIE Cast called to Generate without being initialized first");
      }
      std::stringstream out;
      size_t length = ConvertShapeToLength(fShape);

      // out << SP << ETensorType << " " << OpName << "_attr = "  << fattr << ";\n";
      out << "\n//------ CAST\n";
      out << SP << "for (int id = 0; id < " << length << " ; id++){\n";

      out << SP << SP << "tensor_" << fNY << "[id] = static_cast<"<< fAttrType << ">(tensor_" << fNX << "[id]);\n";

      out << SP << "}\n";
      return out.str();
   }
```
Here `fAttrType` is the data type to which the elements of the input tensor are cast.

- **PR Status**:-

| Pull Request| PR Number |   Status     |
| :---        |    :----:   |          ---: |
| Cast ONNX Operator | [#11033](https://github.com/root-project/root/pull/11033)       | <img src="https://img.shields.io/badge/PR-Merged-blueviolet?style=for-the-badge&logo=appveyor"> |

#### 11) Implemented the Shape ONNX Operator

- **Defination:-** [Shape ONNX Documentation](https://github.com/onnx/onnx/blob/main/docs/Operators.md#Shape)

Shape Operator takes a tensor as input and outputs an 1D int64 tensor containing the shape of the input tensor.

- Code Snippet demonstrating the implementation of Shape Operator in `Generate` function.

```C++
   std::string Generate(std::string OpName){
      OpName = "op_" + OpName;
      if (fShape.empty()) {
         throw std::runtime_error("TMVA SOFIE Shape op called to Generate without being initialized first");
      }
      std::stringstream out;

      out << "\n//------ Shape\n";
      size_t length = ConvertShapeToLength(fOutput_shape);
      for (size_t id = 0; id < length; id++) {
         out << SP << "tensor_" << fNY << "["<< id << "] = " << fShape[fStart+id] << ";\n";
      }
      return out.str();
   }
```
Note that the `fOutput_shape` is determined by `fOutput_shape = { size_t(fEnd - fStart) + 1};`, where `fStart` and `fEnd` are Optional Attributes denoting the Start and end position of input tensor shape, it is used to compute a slice of the input tensor's shape.

- **PR Status**:-

| Pull Request| PR Number |   Status     |
| :---        |    :----:   |          ---: |
| Shape ONNX Operator | [#11086](https://github.com/root-project/root/pull/11086)       | <img src="https://img.shields.io/badge/PR-Merged-blueviolet?style=for-the-badge&logo=appveyor"> |

#### 12) Implemented the Max ONNX Operator

- **Defination:-** [Max ONNX Documentation](https://github.com/onnx/onnx/blob/main/docs/Operators.md#Max)

Max Operator calculates element-wise max of each of the input tensors (with Numpy-style broadcasting support). It also supports multi-directional broadcasting but currently we have support for only the input and output tensors of same length.

- Code Snippet demonstrating the implementation of Max ONNX Operator in `Generate` function.
```C++

   std::string Generate(std::string OpName){
      OpName = "op_" + OpName;
      if (fShape.empty()) {
         throw std::runtime_error("TMVA SOFIE Max called to Generate without being initialized first");
      }
      std::stringstream out;
      size_t length = ConvertShapeToLength(fShape);
      out << "\n//------ Max\n";
      out << SP << "for (size_t id = 0; id < " << length << " ; id++){\n";
      if(fInputNames.size() == 1){
         out << SP << SP <<"tensor_" << fNY << "[id] = tensor_" << fInputNames[0] << "[id];\n";
      }
      else if(fInputNames.size() == 2){
         out << SP << SP <<"tensor_" << fNY << "[id] = std::max({tensor_" << fInputNames[0] << "[id],tensor_" << fInputNames[1] << "[id]});\n";
      }
      else{
         out << SP << SP <<"tensor_" << fNY << "[id] = std::max({";
         size_t j = 0;
         for ( j = 0; j < fInputNames.size()-1; j++){
            out << "tensor_" << fInputNames[j] << "[id],";
         }
         out << "tensor_" << fInputNames[j] << "[id]});\n";
      }
      out << SP << "}\n";
      return out.str();
   }
```

| Pull Request| PR Number |   Status     |
| :---        |    :----:   |          ---: |
| Max ONNX Operator | [#11198](https://github.com/root-project/root/pull/11198)       | <img src="https://img.shields.io/badge/PR-Merged-blueviolet?style=for-the-badge&logo=appveyor"> |

#### 13) Implemented the Reduce ONNX Operators: ReduceMean, ReduceSumSquare, ReduceProd

- **Defination:-** 
1. [ReduceMean ONNX Documentation](https://github.com/onnx/onnx/blob/main/docs/Operators.md#ReduceMean)
It computes the mean of the input tensor's element along the provided axes. The dimension can be reduced or can be of same rank according to the values of attributes provided.
2. [ReduceSumSquare ONNX Documentation](https://github.com/onnx/onnx/blob/main/docs/Operators.md#reducesumsquare)
It computes the sum square of the input tensor's element along the provided axes.The dimension can be reduced or can be of same rank according to the values of attributes provided.
3. [ReduceProd ONNX Documentation](https://github.com/onnx/onnx/blob/main/docs/Operators.md#reduceprod)
It computes the product of the input tensor's element along the provided axes.The dimension can be reduced or can be of same rank according to the values of attributes provided.

- Code Snippet demonstrating the implementation of Reduce ONNX Operators in `Generate` function.
```C++
  std::string Generate(std::string OpName){
      OpName = "op_" + OpName;
      if (fShapeX.empty() || fShapeY.empty()) {
         throw std::runtime_error("TMVA SOFIE Reduce Op called to Generate without being initialized first");
      }

      size_t outputLength = TMVA::Experimental::SOFIE::ConvertShapeToLength(fShapeY);

      auto inputStrides = TMVA::Experimental::SOFIE::UTILITY::ComputeStrideFromShape(fShapeX);
      auto outputStrides = TMVA::Experimental::SOFIE::UTILITY::ComputeStrideFromShape(fShapeY);

      // write here according to size of shape
      // in generation code can be done automatically
      // i0 =  i / s0 ; i1 = (i % s0) / s1 ; i2 = ( (i % s0) % s1 ) / s2 and so on
      // and we have for the inverse
      // i = i0 * s0 + i1 * s1 + i2 * s2 + i3 * s3 ....

      // don't need to divide by last stride s[n-1] since it is 1 by definition

      std::stringstream out;
      out << "\n//----  operator " << Name() << "  " << OpName << "\n";
      out << SP << "for (size_t i = 0; i < " << outputLength << "; i++) {\n";

      size_t dim = fShapeX.size();   // this is the input dimension (e.g. 2, 3 or 4 or more)

      // here we find output indices
      out << SP << SP << "size_t idx_0 = i / " << outputStrides[0] << ";\n" ;
      out << SP << SP << "size_t itmp = i;\n";
      for (size_t k = 1; k < dim; k++) {
         out << SP << SP << "itmp = itmp % " << outputStrides[k-1] << ";\n" ;
         if (k < dim-1)
            out << SP << SP << "size_t idx_" << k << " = itmp / " << outputStrides[k] << ";\n" ;
         else
           // to avoid division by 1 which is outputStrides[dim-1]
           out << SP << SP << "size_t idx_" << k << " = itmp;\n";
      }

      // compute reduction

      if(fReduceOpMode == ReduceProd)
         out << SP << SP << "float sum = 1;\n";
      else 
         out << SP << SP << "float sum = 0;\n";

      out << SP << SP << "for (size_t k = 0; k < " << fShapeX[fAttrAxes] <<"; k++) { \n";
      out << SP << SP << SP << "idx_" << fAttrAxes << " = k;\n";
       // compute input index j
      out << SP << SP << SP << "size_t l = ";
      for(int n = dim-1; n >=0; n--) {
         if (n == int(dim-1))
            out << "idx_" << n;
         else
            out << " + " << "idx_" << n << " * " << inputStrides[n];
      }
      out << ";\n";

      if(fReduceOpMode == ReduceMean){
         out << SP << SP << SP << "sum += tensor_" << fNX << "[l];\n";
         out << SP << SP << "}\n";
         out << SP << SP << "float reduceResult = sum/static_cast<float>(" << fShapeX[fAttrAxes] << ");\n";
      }
      else if(fReduceOpMode == ReduceSumsquare){
         out << SP << SP << SP << "sum += tensor_" << fNX << "[l] * tensor_" << fNX << "[l];\n";
         out << SP << SP << "}\n";
         out << SP << SP << "float reduceResult = sum;\n";
      }
      else if(fReduceOpMode == ReduceProd){
         out << SP << SP << SP << "sum *= tensor_" << fNX << "[l];\n";
         out << SP << SP << "}\n";
         out << SP << SP << "float reduceResult = sum;\n";
      }

      out << SP << SP << "tensor_" << fNY << "[i] = reduceResult;\n";
      out << SP << "}\n";
      return out.str();
   }
```

- **PR Status**:-

| Pull Request| PR Number |   Status     |
| :---        |    :----:   |          ---: |
| Reduce ONNX Operators | [#11258](https://github.com/root-project/root/pull/11258)       | <img src="https://img.shields.io/badge/PR-Merged-blueviolet?style=for-the-badge&logo=appveyor"> |

#### 14) Extend Concat ONNX Operator to implement stack functionality as the ONNX ConcatFromSequence operator

- **Defination:-** [ConcatFromSequence ONNX Documentation](https://github.com/onnx/onnx/blob/main/docs/Operators.md#ConcatFromSequence)

Concatenate a sequence of tensors into a single tensor. All input tensors must have the same shape, except for the dimension size of the axis to concatenate on. By default 'new_axis' is 0, the behavior is similar to numpy.concatenate(). When 'new_axis' is 1, the behavior is similar to numpy.stack().

np.concat() part was already implemented previously in the concat operator , i need to extend the support so it could support np.stack() functionality as well. This was required for GNN testing.

This is the code snippet of implementation of np.stack() functionality when `new_axis` attribute is 1. 
```C++
std::vector<int> stack;
if(fnewAxis == 1){
   for(size_t i = 0; i < inputs.size(); i++) {
      if (i > 0 && inputs[i].size() != inputs[i-1].size() )
      throw std::runtime_error("TMVA SOFIE Concat Op - input tensors have different shapes " +
         ConvertShapeToString(inputs[i]) + " and " + ConvertShapeToString(inputs[i-1]));
      for (size_t iaxis = 0; iaxis < inputs[i].size(); iaxis++) {
         if ((int) iaxis == fAxis)
            stack.push_back(inputs[i][iaxis]);
         else
         if (i> 0 && inputs[i][iaxis] != inputs[i-1][iaxis])
            throw std::runtime_error("TMVA SOFIE Concat Op - input tensors have wrong shapes " +
            ConvertShapeToString(inputs[i]) + " and " + ConvertShapeToString(inputs[i-1]));
      }

   }
   for(auto it:stack)
   ret[0].push_back(it);
}
```

- **PR Status**:-

| Pull Request| PR Number |   Status     |
| :---        |    :----:   |          ---: |
| Extend Concat ONNX Operator to implement stack functionality as the ONNX ConcatFromSequence operator | [#11317](https://github.com/root-project/root/pull/11317)       | <img src="https://img.shields.io/badge/PR-Merged-blueviolet?style=for-the-badge&logo=appveyor"> |

## Some Useful Blogs written by me.
1) [Python Tutorials for various C files of Tutorials/TMVA](https://gist.github.com/Neel-Shah-29/7e46bee55f7c09a18e94696a0a3e5ccf)
2) [Documentation on RModelParser_ONNX.cxx](https://gist.github.com/Neel-Shah-29/5c1399ccd23903928128822c6f3e0957)
3) [Getting into GSOC 2022](https://gist.github.com/Neel-Shah-29/3f04f05a8a353605068e32e55a5093c1)
4) [All about Community Bonding Period](https://gist.github.com/Neel-Shah-29/b2c887adaa118ba68b42e324d3b2a47a)
5) [Implementing the Operators in Sofie](https://gist.github.com/Neel-Shah-29/f0371566ca1e24a6b3a9b4097cdd44db)

## Conclusion
I enjoyed a lot working with these project! I would like to really thank my mentors **Lorenzo Moneta, Sitong An, Omar, Ahmat Hamdan and Sanjiban Sengupta** for always being a great support for me. Whenever i wanted any help or guidance, they were always with me! I am very proud to be associated with so many bright minds surrounded by me, and every single day i learn something new from them. At the end i am able to achieve all of my success because of the best wishes of my parents, seniors and friends so a big thanks to them as well.

Hope you all enjoyed reading my blog and learnt a lot.

**Thanks and Regards,**

**Neel Shah**
