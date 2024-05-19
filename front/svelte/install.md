## 创建项目

```shell
## 创建项目
npm create svelte@latest open-webui

cd open-webui
# 安装依赖
yarn 

## 增加tailwindcss样式
npx svelte-add@latest tailwindcss

## 增加shadcn-svelte依赖
npx shadcn-svelte@latest init


## 增加一个组件
npx shadcn-svelte@latest add button


npx shadcn-svelte@latest add  progress
npx shadcn-svelte@latest add scroll-area
```

### 依赖说明

1、lucide-svelte [Installation | Lucide](https://lucide.dev/guide/installation)

> Lucide是一个开源图标库，提供了1000多个矢量（SVG）文件，用于在数字及非数字项目中展示图标和符号。该库旨在通过提供多个官方包，使设计师和开发者能更轻松地将图标融入他们的项目中，从而简化了在项目中使用这些图标的流程。

2、mdsx [Introduction - MDSX](https://mdsx.dev/docs)

> 撰写内容本就不易，而在HTML中撰写内容更是难上加难。Markdown是一种优秀的写作格式，但它有时并不能满足所有需求。有时，你可能需要为内容增添一点交互性，或是需要在交互元素中嵌入一些内容。这时，MDSX就派上了用场。
> 
> MDSX是专为Svelte设计的Markdown预处理器，它架起了Markdown与组件之间的桥梁。你可以用它来编写Markdown文件，进而导入到Svelte组件中，或者反向操作，将Svelte组件导入Markdown文件里。

3、
