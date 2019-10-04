<template>
  <styled-item :is-grid="viewMode.isGrid" :theme-color="theme.defaultColor">
    <img :src="src">
    <styled-item-title :is-grid="viewMode.isGrid" :theme-color="theme.defaultColor">{{title}}</styled-item-title>
  </styled-item>
</template>
<script>
import yiq from "yiq";
import { darken } from "polished";
import styled, { css } from "vue-styled-components";

const itemProps = {
  isGrid: Boolean,
  themeColor: String
};

const TitleRowStyle = css`
  border: none;
  font-size: 18px;
  margin-left: 10px;
  line-height: 2;
`;

const StyledItemTitle = styled("h3", itemProps)`
  color: ${props => yiq(props.themeColor)};
  margin: 0;
  padding: 0.8rem 0;
  border-top: ${props => (props.isGrid ? "1px solid lightgray" : "none")};
  ${props => (props.isGrid ? null : TitleRowStyle)}
`;

const Card = css`
  margin-right: 10px;
  margin-bottom: 10px;
  width: 220px;
  box-shadow: 0 1px 2px rgba(0, 0, 0, 0.2);
`;

const Row = css`
  min-height: 60px;
  display: flex;
  width: 100%;

  img {
    height: 60px;
  }
`;

const StyledItem = styled("div", itemProps)`
  border: 1px solid lightgray;
  padding: 5px;
  background: ${props => props.themeColor};

  ${props => (props.isGrid ? Card : Row)}

  &:hover {
    background-color: ${props => darken(0.05, props.themeColor)};
    cursor: pointer;
  }
`;

export default {
  inject: ["viewMode", "theme"],
  components: { StyledItem, StyledItemTitle },
  props: {
    title: String,
    publicId: String,
    cloudName: String
  },
  computed: {
    src() {
      return `https://res.cloudinary.com/${this.cloudName}/image/upload/${
        this.publicId
      }.png`;
    }
  }
};
</script>