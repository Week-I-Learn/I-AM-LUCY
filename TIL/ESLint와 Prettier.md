```text
오늘은 팀 내 standard repository 작업을 하면서 설정했던 ESLint와 Prettier에 관하여 작성하려고 한다.  
프로젝트 진행 시, 코드의 유지 보수와 협업을 용이하게 하기 위해 있어 통일된 문법 즉, 코딩 컨벤션을 가지고 작업하게 된다. 
이 과정에서 ESLint, prettier가 문법적 오류나 팀원 간의 협의된 코딩 컨벤션을 자동으로 확인하고 적용해 주어 작업 효율을 증가시킬 수 있다. 
```
- [ ] <strong> ESLint는 보다 좋은 품질의 자바스크립트 코드를 작성하기 위한 일종의 코드 스타일 가이드다. </strong> 
- [ ] <strong> Prettier란 원본 스타일을 모두 제거하고 출력되는 모든 코드가 일관된 스타일을 준수하도록 만들어주는 도구이다.</strong>

<br/>

### Next.js, TypeScript project에 ESLint와 Prettier 설정하기

```
// 프로젝트 생성
npx create-next-app ./

// config 파일 생성
touch tsconfig.json

// 프로젝트 실행
npm run dev

// typescript를 설치하라는 다음과 같은 메시지가 출력됩니다. 
// Please install typescript and @types/react by running: npm install --save-dev typescript @types/react

// @types/react-dom, @types/node를 추가하여 설치합니다.
npm install --save-dev typescript @types/react @types/react-dom @types/node

// 프로젝트 실행 및 정상 작동 확인
npm run dev
```

#### tsconfig.json
절대경로 임포트를 위하여 baseUrl를 .(root)로 설정, strict를 true 설정하여 더 빡빡한 type checking으로 변경합니다.
```json
{
  "compilerOptions": {
    "baseUrl": ".",  
    "target": "es5",
    "lib": ["dom", "dom.iterable", "esnext"],
    "allowJs": true,
    "skipLibCheck": true,
    "strict": true,
    "forceConsistentCasingInFileNames": true,
    "noEmit": true,
    "esModuleInterop": true,
    "module": "esnext",
    "moduleResolution": "node",
    "resolveJsonModule": true,
    "isolatedModules": true,
    "jsx": "preserve"
  },
  "include": ["next-env.d.ts", "**/*.ts", "**/*.tsx"],
  "exclude": ["node_modules"]
}
```

#### ESLint 
아래 명령어를 통하여 ESLint 셋팅을 설정해줍니다.
```
npx eslint --init
✔ How would you like to use ESLint? · problems
✔ What type of modules does your project use? · esm
✔ Which framework does your project use? · react
✔ Does your project use TypeScript? · Yes
✔ Where does your code run? · browser, node
✔ What format do you want your config file to be in? · JavaScript

eslint-plugin-react@latest @typescript-eslint/eslint-plugin@latest @typescript-eslint/parser@latest
✔ Would you like to install them now? · No / Yes
✔ Which package manager do you want to use? · npm
Installing eslint-plugin-react@latest, @typescript-eslint/eslint-plugin@latest, @typescript-eslint/parser@latest
```

제가 설정한 .eslintrc.js 파일 내용입니다. 본인 프로젝트에 알맞제  추가, 삭제하여 사용해주세요 :)
```
module.exports = {
  env: {
    // 전역 변수 사용을 정의합니다. 추가하지 않으면 ESLint 규칙에 걸리게 됩니다.
    browser: true,
    es6: true,
    node: true,
  },
  extends: [
    'eslint:recommended',
    'plugin:react/recommended',
    'plugin:@typescript-eslint/recommended', // 해당 플러그인의 권장 규칙을 사용합니다.
    'plugin:prettier/recommended', // plugin과 eslint-config-prettier 설정을 한번에 합니다.
  ],
  parser: '@typescript-eslint/parser', // ESLint 파서를 지정합니다.
  parserOptions: {
    ecmaFeatures: {
      jsx: true, // JSX를 파싱할 수 있습니다.
    },
    ecmaVersion: 12, // Modern ECMAScript를 파싱할 수 있습니다.
    sourceType: 'module', // import, export를 사용할 수 있습니다.
  },
  plugins: ['react', '@typescript-eslint'],
  rules: {
    // ESLint 규칙을 지정합니다. extends에서 지정된 규칙을 덮어 쓸수도 있습니다.
    'react/react-in-jsx-scope': 'off',
    'react/prop-types': 'off',
    '@typescript-eslint/no-explicit-any': 'off', // any 타입을 사용할 수 있습니다.
    '@typescript-eslint/explicit-module-boundary-types': 'off', // 함수의 반환 타입을 지정할 수 있습니다.
    '@typescript-eslint/no-var-requires': 'off', // require를 사용할 수 있습니다.
    '@typescript-eslint/no-empty-function': 'off', // 빈 함수를 사용할 수 있습니다.
    '@typescript-eslint/ban-types': 'off', // 타입을 지정할 수 있습니다.
  },
  settings: {
    react: {
      version: 'detect', // 현재 사용하고 있는 react 버전을 eslint-plugin-react가 자동으로 감지합니다.
    },
  },
};

```

#### Prettier
.prettierrc.js 파일을 생성하고, 원하시는 조건을 추가해줍니다 :)
```
module.exports = {
  semi: true,
  trailingComma: 'all',
  singleQuote: true,
  printWidth: 80,
  tabWidth: 2,
};
```
```
npm install --save-dev prettier eslint-config-prettier eslint-plugin-prettier
```

[TypeScript ESLint Rules](https://typescript-eslint.io/rules/)
